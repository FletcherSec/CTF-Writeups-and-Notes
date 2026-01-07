- You can version your files in [[S3]]
- It is enabled at the bucket level
- Same key overwrite will change the "version": 1, 2, 3...
- It is best practice to version your buckets
	- Protect against unintended deletes (ability to restore a version)
	- Easy roll back to previous version
- Notes:
	- Any file that is not versioned prior to enabling versioning will have version "null"
	- Suspending versioning does not delete the previous versions

Deleting objects themselves via Delete with Delete Objects just makes an empty object that can be reversed (allows rolling back to original version via deleting delete marker)