# Getting started

## First time setup for your ansible control system

These are the steps to setup your ansible control system once off and
get started with our ansible setup.

1.  Install initial requirements:

    MacOS:

    ```bash
    xcode-select --install
    brew install python@3.14 git ansible
    ```

1.  Clone the git repository somewhere. Something like

    ```bash
    mkdir -p ~/src/work
    cd ~/src/work/
    git clone git@github.com:ashleykleynhans/ansible.git
    cd ~/src/work/ansible
    ```

1.  If you had already cloned the repository, ensure you have pulled
    the latest code and have checked out `main` branch.

    ```bash
    cd ~/src/work/ansible
    git checkout main
    git pull origin main
    ```

1.  Setup python environment, activate it.  Then upgrade pip and fetch
    your python requirements.

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate
    pip install --upgrade pip
    pip install -r requirements.txt
    ```

    When you want to later unset your python virtual environment,
    simply run `deactivate`, or logout of the shell.

    Running `which ansible` should show something like this now:

    ```bash
    [ashley:~] [ansible] % which ansible
    /Users/ashley/src/work/ansible/.venv/bin/ansible
    ```

    !!! important
        Take note that anytime in future, when you want to
        interact with ansible, you will need to setup your shell
        environment by simply running `source ./venv/bin/activate`.

1.  Run the below to fetch all our external role requirements.

    ```bash
    ansible-galaxy install -r roles_external/requirements.yml
    ```

    !!! important
        You will need to rerun this command anytime the `roles_external/requirements.yml`
        file is updated.

1.  You can obtain the vault passwords from a one of your team mates.
    You then need to populate the vault file on your ansible controller.
    There is currently two vaults, `test` and `prod`.  Only the DevOps
    engineers should have access to the `prod` vault.

    For test:
    ```bash
    echo 'the_test_password' > vault/vault-test.txt
    ```

    For prod:
    ```bash
    echo 'the_prod_password' > vault/vault-prod.txt
    ```

## How to typically run a playbook

1.  Ensure you are in the root of the code base when you run your
    playbook. Secondly you need to always source the python
    environment into your shell before calling ansible. Example:

    ```bash
    cd ~/src/work/ansible
    source .venv/bin/activate
    ```

1.  Each playbook run should be accompanied by passing in the
    inventory file and the vault file.  These are specific to an
    environment. For example:

    ```bash
    ansible-playbook \
      --vault-id test@vault/vault-test.txt \
      -i inventories/manual_inventory_test.ini \
      playbooks/some_playbook.yml
    ```

    Or for prod
    ```bash
    ansible-playbook \
      --vault-id prod@vault/vault-prod.txt \
      -i inventories/manual_inventory_prod.ini \
      playbooks/some_playbook.yml
    ```

1.  Typically you should read through the playbook before using it to
    understand what it's doing.  Most importantly to understand on
    which hosts on the environment it is running on.

1.  Further more it can be useful to limit the playbook to certain
    hosts.  See the `--limit` documentation.  It too supports regex.
