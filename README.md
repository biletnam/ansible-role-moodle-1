# Ansible Role: Moodle

Installs Moodle (3.0+) on RedHat and Debian/Ubuntu servers.
Tested with Ansible 2.5

## Requirements

Needs to be a recent LTS release of Ubuntu or REL which have PHP 7.0+, Apache 2.4 and 
Postgres or Mysql installed.
 

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

## Role Tags

You can skip installation steps by just doing:
    
    ansible-playbook <playbook>.yml --skip-tags "install"

Or change password by:
    ansible-playbook <playbook>.yml --skip-tags "install" --tags "task-pw"
    
Possible tag for direct tasks:
- task-pull: will refresh the code
- task-pw: will change password


## Dependencies

No dependencies if the host is installed and setup with a LAMP stack 
( or similar ) environement.
If you are required to install the full environment, I suggest you check:
 - geerlingguy.php (Install of PHP 7.x or earlier)
 - geerlingguy.apache (Installation of Apache 2.x)
 - geerlingguy.postgresql (Installation of Postgres)
 - geerlingguy.mysql (Installatiion of Mysql)

## Example Playbook

## License

MIT / BSD

## Author Information

This role was created in 2017 by [Laurent David](https://github.com/laurentdavid), from 
[Jeff Geerling](https://www.jeffgeerling.com/) roles templates author of 
[Ansible for DevOps](https://www.ansiblefordevops.com/).


## Testing

We have used Jeff Geerling's tests as a base, so:

- Test should run on travis  
- Locally you can start the test process using the command

        ./tests/test_local.sh
    
    The docker instance is destroyed at the end of the test, but you can keep it by setting the
     environment variable "cleanup" to "false":
     
        cleanup="false" ./tests/test_local.sh
     
- Once the docker has been launch you can rerun the playbook by running:
```bash
    container_id=xxxxyyy
    docker exec --tty $container_id env TERM=xterm ansible-playbook /etc/ansible/roles/role_under_test/tests/test.yml
```

Prerequisites are to have docker installed locally.
It will run the tests on postgresql only. More info in the README.md file in the tests folder.

### Library testing
There is a small module that checks if moodle is installed/configured in the library folder.
More info in the README.md of the library folder.
