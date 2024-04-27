# Cloud Storage

## Why Cloud Storage is a popular choice to serve as a data lake

- Data persists beyond the lifetime of VMs (persistant)
- Relatively inexpensive compared to cost of compute [Eg: Cache the results of previous compute, Dont need the application running;then store the state and close application]
- It is object store, so it just stores and retrives binary objects without regard of what the data is
- Similar to file system - so we can copy and move files around
- Data stored in durable and also instantly available with consistency
- Share data globally, but can be encrypted and kept private as well if needed.
- Data accessed from anywhere and can be kept anywhere in a single geographic location if needed

## How does Cloud Storage work

- Two entities: Buckets and Objects
- Buckets are containers for objects
- Objects exists inside of buckets and not apart from them
- Buckets are global namespaced scope (only one name across the global scope)
- bucket is associated to a region or multiple regions
- Choosing region close to data processing resource will save us on network egress charges and also reduce latency
- When object stored, Cloud Storage replicates object. If one of the copy is corroupted then it is replaced with a fresh copy.
- For multi-region bucket, the objects are replicated across regions and for single region, they are replicated across zones.
- Object is served from closest replica to requestor. Multiple requesters could be retrieving the objects at the same time from different replicas. (high availability)
- Objects are stored with metadata (Access Control, Compression, Encryption, Lifecycle Management)
- For example, Cloud Storage knows when an object was stored, and it can be set to automatically delete after a period of time. This feature uses the object metadata to determine when to delete the object.

## Overview of Storage Classes

![Alt text](./Storage-classes.png)

## Cloud Storage - Simulation of File System

- Syntax: BucketName/ObjectPath
- BucketName is unique to the global namespace
- Cloud Storage works like file systems with following differences
- For example, imagine that we wanted to move all the files in the 02 directory to the 03 directory inside the modules directory.
- In a file system we would have actual directory structures and we would simply modify the filesystem metadata, so that the entire move is atomic.
- But in an object store simulating a file system, we would have to search through all the objects contained in the bucket for names that had "02" in the right position in the name. Then we would have to edit each object name and rename them using 03. This would produce apparently the same result; moving the files between directories. However, instead of working with a dozen files in a directory, the system had to search over possibly thousands of objects in the bucket to locate the ones with the right names and change each of them. So the performance characteristics are different.
- It might take longer to move a dozen objects from directory 02 to directory 03 depending on how many other objects are stored in the bucket.
- During the move, there will be list inconsistency, with some files in the old directory and some in the new directory.
**A best practice is to avoid the use of sensitive information as part of bucket names because bucket names are in a global namespace.**

## Cloud Storage - Management Features

- For example, we can set a retention policy on all objects in the bucket. For example, the objects should expire after 30 days.
- You can also use versioning, so that multiple versions of an object are tracked and available if necessary.
- You might even set up lifecycle management, to automatically move objects that haven’t been accessed in 30 days to Nearline and after 90 days to Coldline.
