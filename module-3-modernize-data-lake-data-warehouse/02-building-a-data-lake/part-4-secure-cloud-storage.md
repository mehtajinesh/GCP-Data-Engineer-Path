# Securing Cloud Storage

- Two methods
  - IAM (Identity Access Management)
  - Access Control Lists

## IAM

- Set at the bucket level and is applied uniform across all objects within a bucket

## Access Control Lists (ACL)

- Can be applied at a bucket level or an individual objects level
- provides more fine-grained access control

## Roles from IAM

- Bucket Level Roles: Reader, Writer, Owner and Set ACL Policy
- Project Level Roles: Create or Delete Bucket
- When creating bucket, we have option to disable ACP List and use IAM Only
- ACL Lists are enabled by default

## Encryption

- All data in Google Cloud in encrypted by default
    1. Automatic Behavior by Google (Google-managed encryption keys, or GMEK)
        - Two levels of encryption:
            - Data is encrypted using encryption key,
            - The encryption key is encrypted using Key Encryption Key, KEK, These are automatically rotated  on a schedule and stored in Cloud Key Management Service
    2. Customer-managed encryption keys, or CMEK
        - we can control the creation and existence of the KEK that is used.
    3. CSEK, or customer-supplied encryption keys
        - use depends on business, legal and regulatory requirements
    4. Client-side encryption
        - we have encrypted the data before it is uploaded and have to decrypt the data yourself before it is used.
        - Cloud Storage still performs GMEK, CMEK or CSEK encryption on the object.
        - It has no knowledge of the extra layer of encryption you may have added.

## Logging of data access, Holds and Locks

- For audit purposes, we can place a hold on an object, and all operations that could change or delete the object are suspended until the hold is released.
- We can also lock a bucket, and no changes or deletions can occur until the lock is released.
- Lock retention policy: continues to remain in effect and prevent deletion, whether a bucket lock or object hold are in-force or not.
- locking prevents them from modifying the data.

## Other Features of Cloud Storage

- Decompressive Coding
  - By default, the data we upload is the same data we get back from Cloud Storage.
  - This includes gzip archives, which usually are returned as gzip archives.
  - However, if we tag an object properly in metadata, we can cause Cloud Storage to decompress the file as it is being served.
  - Benefits of the smaller compressed file are faster upload and lower storage costs compared with the uncompressed files.
- Requester Pay
  - if data is accessed from a different region, we will have to pay network egress charges, but we can make the requester pay so that we pay only for data storage.
- Anonymous Sharing
  - We can create a signed URL to anonymously share an object in Cloud Storage, and even have the URL expire after a period of time.
- Composite Object
  - upload an object in pieces and create a composite object without having to concatenate the pieces after upload
