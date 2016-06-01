Webhop - Bootstrap Drupal for Vagrant
======================================

Ansible role to install requirements and backup for a drupal site into a vagrant machine


## Requirements

Requires a working python 2.7 installation in the base vagrant box being used


## Role Variables

##### Defaults

- `drupal_mysql_user` - User to create in the mysql database for drupal. (**drupal**)
- `drupal_mysql_password` - Password to set in mysql for drupal. (**drupal**)
- `drupal_mysql_database` - MySQL database name for drupal database. (**drupal**)
- `doc_root` -  Full path to the website file dir. (**/var/www**)
- `memcache_key_prefix` - Memcache key prefix to use. (**drupalvagrant**)
- `restore_db_backup` - Restore DB archive from s3. (**false**)
- `restore_files_backup` - Restore files archive from s3. (**false**)
- `region` - When restoring the DB and/ or files use this region in s3 for the fetch operation (**eu-central-1**)
- `s3_bucket` - S3 bucket name if a restore action is required (**webhop-migration-backups**)
- `drupal_install_profile` - The installation profile to use. (**minimal**)


##### Variables

- `database_backup_name` - Database archive object name in the s3 bucket
- `files_backup_name` - Files archive object name in the s3 bucket


Usage
-----

```yaml
roles:
    - { role: webhop.bootstrap-drupal-vagrant,
        database_backup_url: https://s3.amazonaws.aws.com/sites/backups/mysite.zip,
        restore_db_backup: true
    }
```

Author Information
------------------

* Neil Saunders - neil@beamly.com
* Vik Bhatti - vik@beamly.com
