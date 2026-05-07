# 🔍 `slt` aka Scott's Lookup Table

`slt` is a script to read data from a key/value text file and print it
out. This is useful for scripting repeatable commands where you do *not* want
to include sensitive data in your history.

### 📦 Installation

Copy the `slt` binary into your `$PATH` and make sure it is executable.

### 📊 Datastore format

The format for the `slt` datastore is a key/value text file. See
`datastore_example.txt` for a syntax examples. The file format is based on
simplified `.ini` format and is designed to be _human_ readable.

### ✨ Usage

```
slt [input.txt] lookup_key

slt /tmp/input.txt username
slt ~/.creds.txt db_password

# Verify your datastore is processed correctly
slt datastore_example.txt --debug

# slt defaults to ~/.slt.txt if no datastore is specified
slt username
```

### 🌎 Real world examples
```
ssh $(slt /tmp/info.txt user)@$(slt /tmp/info.txt ip)

# Avoid storing the password in your bash history
mysql --user jason --database my_db --password=$(slt /tmp/creds.txt passwd)

# Simplify commands by using leaving off datastore which defaults to ~/.slt.txt
ping $(slt ip)

# Use an enviroment variable for the datastore file
export SLT_FILE=/tmp/myds.txt
vim $(slt book)
```
