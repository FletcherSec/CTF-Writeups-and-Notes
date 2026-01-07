EBS to move to a different availability zone you must:
- Make a snapshot of an EBS attached to zone 1 and restore the EBS in zone 2 from the EBS snapshot you created
- this is a copy and NOT in sync

EFS is a network file system that is shared by everything mounted to it:
- All availability zones mounting the EFS simultaneously access it

EFS Infrequent Access [[EFS-IA]]:
- Storage class that is cost-optimized for files not accessed every day
- Up to 92% lower cost compared to EFS Standard
- EFS will automatically move your files to EFS-IA based on the last time they were accessed
- Enable EFS-IA with a [[Lifecycle Policy]]
- Example: move files that are not accessed for 60 days to EFS-IA
- Handled behind the scenes, transparent to the applications accessing [[EFS]]