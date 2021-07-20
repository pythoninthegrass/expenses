Expenses
========

Expenses is a tiny expense tracker written in Python.

```
expenses add 3.10 "Cappuccino at Dark Horse"
expenses summary
expenses plot
```

Features
--------

- Stores expenses in a very simple CSV file
- Keeps a full version history of expenses in case of user error
- Supports basic reports and plotting of expenses

Setup
----------------
Expenses itself is contained in a single executable. Put that in your PATH somewhere. Dependencies:
- Python 3.9+
- Matplotlib (If you want to use the plot feature)
- Github CLI (`gh`)

## Python and dependencies
* Install (OS)
  * [brew](https://brew.sh/)
  * python3.9: `brew update && brew install python3`
  * [pip](https://pip.pypa.io/en/stable/installing/): `python get-pip.py`
  * [pipenv](https://pipenv.pypa.io/en/latest/): `pip install --user pipenv`
* ENV vars
  * To run script within `pipenv`, need to set [environment variables](https://github.com/odemeniuk/playwright-py/actions/runs/192428516/workflow)
    ```bash
    export VENV_HOME_DIR=$(pipenv --venv)
    source $VENV_HOME_DIR/bin/activate
    export PYTHONPATH="$PYTHONPATH:."
    ```
* Install (libraries)
  ```bash
  pipenv install --python 3.9 matplotlib python-decouple
  ```

## Install gh
```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg
| sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyring
s/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" |
sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```
Usage
----------------

When you type "expenses" on the command-line for the first time, a new Expenses setup
is created at `~/.expenses/`. This includes a mercurial repository at `~/.expenses/repo`
which contains your actual expenses file `~/.expenses/repo/expenses.csv`.

You probably won't need to work with that file directly, you can use the `expenses list`
command to view it, and the `expenses edit` command to edit it. By using those commands
you ensure that it stays properly versioned.

TODO
----------------
* Copy/pasta Linux pipenv/pyenv instructions from another castle
* Remove mercurial
* Implement `gh` via subprocess
* **Usage**: wrapper for pipenv and/or package w/Poetry
