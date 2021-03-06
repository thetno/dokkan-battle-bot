# Dragon Ball Dokkan Battle Bot

This is a Dokkan Battle bot that was first created by FlashChaser. I added a lot of new features and planning on adding more, therefore I've created my own repo. 
There's no support from me - it is what it is. If you're gonna get banned - bad luck. 

If you want to add a feature you've made feel free to submit a pull request.

The bot is made quite straightforwardly:
The packet module handles the encryption of packet data as well as the authorisation.
There shouldn't be too much reason to add to this file beyond fixing bugs.

The commands module is where the bulk of the code will be written for adding new features.

The dokkan module is where the command line/UI will be implemented, and will call the functions in the commands module.

The decryptor module uses: https://github.com/bssthu/pysqlsimplecipher
Although it's slow FlashChaser preferred this code over pysqlcipher simply because it's easier to package it for distribution without running into issues.

# Download
Just grab a copy of master repo and go on.

# Installation

You might need to use sudo before every pip3 command.

```pip3 install six
pip3 install pyinstaller
pip3 install colorama
pip3 install orator
pip3 install pycryptodome
pip3 install PySimpleGUI
pip3 install requests
```
Then go to folder where your dokkan.py file is and: python3 dokkan.py

Happy testing!

# Pull Requests
Very happy to merge pull requests.
Until I can develop some tests be careful to make sure that all new commands that you implement accurately support JP translation.

e.g Check that you read from the global database, and if the data doesn't exist, read from the jp database.

```python
try:
    config.Model.set_connection_resolver(config.db_glb)
    config.Quests.find_or_fail(int(stage_id))
except:
    config.Model.set_connection_resolver(config.db_jp)
    config.Quests.find_or_fail(int(stage_id))
```
