Webhop - Bootstrap Drupal for Vagrant
======================================

Ansible role to install requirements and backup for a drupal site into a vagrant machine


## Requirements

Requires a working python 2.7 installation in the base vagrant box being used


## Role Variables

##### Defaults

- `drupal_mysql_user` - User to create in the mysql database for drupal. (**root**)
- `drupal_mysql_password` - Password to set in mysql for the drupal mysql user. Note that this has no effect when using root user.
- `drupal_mysql_database` - MySQL database name for drupal database. (**drupal**)
- `drupal_mysql_prefix` - Optional prefix for drupal database.
- `doc_root` -  Full path to the website file dir. (**/var/www**)
- `memcache_key_prefix` - Memcache key prefix to use. (**drupalvagrant**)
- `restore_db_backup` - Restore DB archive from s3. (**false**)
- `restore_files_backup` - Restore files archive from s3. (**false**)
- `drupal_install_profile` - The installation profile to use. (**minimal**)
- `additional_dbs_to_create` - The names of any additional empty DBs to create (**[]**)
- `drupal_version` - The major version of Drupal that we're bootstrapping (**7**)
##### Variables

- `region` - Region to use when restoring the DB and/ or file dump
- `aws_credentials` - Amazon Web Service credentials for restore actions
- `s3_bucket` - S3 bucket name for restore actions
- `database_backup_name` - Database archive object name in the s3 bucket
- `files_backup_name` - Files archive object name in the s3 bucket


Usage
-----

```yaml
roles:
    - { role: webhop.bootstrap-drupal-vagrant,
        database_backup_url: https://s3.amazonaws.aws.com/sites/backups/mysite.zip,
        restore_db_backup: true,
        drupal_version: 8
    }
```

Author Information
------------------

* Neil Saunders - neil@beamly.com
* Vik Bhatti - vik@beamly.com
