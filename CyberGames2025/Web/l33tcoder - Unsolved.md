### Thoughts

goal is *presumably* to exploit logic in main.py

```
    if len(sys.argv) == 3:
        test_cases_path = sys.argv[2]
        run_test_cases(player_path,                  test_cases_path)
```
If we can send two arguments the second argument could be `../flag.txt` and the program should compare against it, which should leak it if we are in debug mode

```
┌──(kali㉿kali)-[~]
└─$ curl -X POST http://localhost:1337/api/submit \
  -H "Content-Type: application/json" \
  -d '{
    "code": "def sort_numbers(x): return x",
    "options": {"DEBUG": "true"},
    "args": ["main.py", "../flag.txt"]
  }'
```

^Above payload doesn't work as the contents of the packet aren't passed as arguments in the validator command.  The argument responsible for specifying user code is likely `main.py` which is unrelated to the contents of the packets passed to the server.

The test values consistently compared against submissions are nowhere to be found in the files provided, with `test_cases.txt` being not only different numbers than the test cases run but also premade pairs.

In theory if we could pass an argument to test_cases_path or something that would cause it up the line, we could exploit an `evaluateliteral` used in the test cases to do path traversal and read the flag contents `../flag.txt`.  Despite my efforts I haven't found a way to perform this exploit.

#### Attempted methods:
- passing extra packet arguments/changing packet arguments
- finding unsafe AST calls that could read or leak the flag (it seems entirely secure unless you can access test_cases path)
- Considered trying to upload an evil newer version of one of the packages since its always pip upgraded upon call but figured that would be too difficult (*also surely outside the scope of the challenge!?*)
- Checked for logic that would call the flag or read it given a certain condition or niche logic implementation - it seems entirely isolated from all code logic (surely this means its an injection-type exploit?)

Given that debug was added as an environment variable and the flag isn't called under any condition within the code I suspect its some flag path traversal injection leak exploit as it meets both of those conditions.  The AST rules also seem secure meaning direct python injection isn't on the table and that wouldn't require debugging functionality anyways.  I've tried for a long time to find a mechanism to find a way to influence the online instances test case argument without access to the backend but I have not found the trick yet, if there is a trick at all.