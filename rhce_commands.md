## Commands
-----

- `sudo subscription-manager repos --list` : Outputs a list of available repos.
- `sudo subscription-manager repos --enable ansible-automation-platform-XX` : Repo required for the automation platform. X is the most current version number.

- `ansible -i inventory all -u username -k -b -K -m user -a "name=ansible"`: -i looks for the inventory file locally. all targets all the hosts in the inventory file. -u specifies the useraccount that is going to perform operations on the managed nodes. -k going to prompt for a password and is used in lieu of ssh keys. -b runs the command as priviledged user. -K asks for priviledged password. -m specifies ansible module. -a specifies arguments that the module will take.

- `ansible -i inventory group --list-hosts`: Lists all hosts in the ansible inventory from the group group. 

- `ansible-navigator inventory -i inventory -m stdout --list`: The ansbile navigator command for the same.
- `ansible-navigator images`: Lists available ansible images that can be used for executing ansible playbook.
- `ansible-navigator doc -m stdout modulename`: Gives information about the specific module. -m stdout displays the information on the terminal rather than in ansible navigator.
- `ansible-navigator --pp never`: Changes the pull policy to never. Ansible navigator nevel looks for newer container images.
    - `:collections` : While in navigator displays all of the collections to you
- `ansible-navigator run -m stdout --pp never playbook.yml` : Runs playbook.yml in ansible-navigator. --pp never sets the pull policy to never. -m stdout will write to stdout instead of using interactive mode.

- `ansible-doc`: Provides documentation about everything ansible.
- `ansible-doc -l`: Lists available modules.
- `ansible-doc -t itemtype item`: Gives information about specific items. -t is an option parameter to specify the item type

- `ansible-galaxy collection install my.collection -p collections`: Installs new collectionsf where my.collection is the collection. -p collection is the collection path. -p is necessary while using execution environments.
- `ansible-galaxy collection list`: GIves a list of available collections with their version number and the locations
- `ansible-galaxy collection install -r collections/requirements.yaml -p /location/of/project` : Installs all required collections for a project. -r specifiies the location of the requirements file. -p specifiies the location of the project.
- `ansible-galaxy role install -p mypath` : Installs a particular role from ansible galaxy. -p specifies installation path.
- `ansible-galaxy [role] search 'docker' --author authorname --platforms platform name` :
- `ansible-galaxy [role] info authorname.role` : Shows info about the role
- `ansible-galaxy install -r requirements.yml` : Installs roles based on the requirements file. 
- `ansible-galaxy init project name` : Creates the custom directory structure for roles.

- `ansible-playbook playboook.yml -v[vvv]` : Executes playbook.yml. -v specifies the level of verbosity.
- `ansible-playbook --ask-vault-pass playbook.yml`: Runs a playbook but directions ansible to ask for passwords required for the vaulted file.
- `ansible-playbook --vault-password-file=location/of/the/file playbook.yml` : Runs the playbook but provides a file with a password to the vaulted file. Allows for not entereing the password manually.


- `ansible-vault create parentdir/secrets.yml` : Creates an encrypted secrets file.
                    `encrypt` : Encrypts an existing file.
                    `decrypt` : Decrypt an existing file.
                    `rekey`   : Change the password on an encrypted file.
