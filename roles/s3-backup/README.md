S3-Backup
=========

## TO DO:

[ ] Make less this about backing up PosgreSQL database

## About: 
Installs AWS toolset and a script to backup a PostgreSQL database. You should provide only enough access to your IAM user to upload to the bucket of your choice.

An example policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1622959131123",
      "Effect": "Allow",
      "Action": [
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
      "Resource": [
        "arn:aws:s3:::your-bucket-name/*"
      ]
    }
  ]
}
```

Role Variables
--------------

Just the AWS config file needs:

* aws_access_key_id
* aws_secret_access_key
* region
* output

As well as items for the backup script:

* bucket_name
* db_name

This assumes PostgreSQL is installed and the script is run as superuser (and system user) `postgres`.

Dependencies
------------

Requires "anisble-pgsql-example" repository, which ensures the `postgres` user exists on the system.