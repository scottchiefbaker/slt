# 🔍 `slt` aka Scott's Lookup Table

`slt` is a simple script to read data from a key/value text file. It's useful
for scripting repeatable commands where you do not want to include the data
in your history.

### 📦 Installation

Copy the `slt` binary into your `$PATH` and make sure it is executable.

### 📊 Datastore format

The format for the `slt` datastore is a key/value text file separated by
either `=` or `:`. See the `datastore_example.txt` for an example file. The
file format is based on simplified `.ini` format.

### ✨ Usage

```
slt [input.txt] [lookup_key]

slt /tmp/input.txt username
slt /tmp/creds.txt db_password

# Verify your datastore is processed correctly
slt datastore_example.txt --debug

# slt defaults to /tmp/slt.txt if no datastore is specified
slt username
```

### 🌎 Real world examples
```
ssh $(slt /tmp/info.txt user)@$(slt /tmp/info.txt ip)

# Avoid storing the password in your bash history
mysql --user jason --database my_db --password=$(slt /tmp/creds.txt passwd)

# Simplify commands by using leaving off datastore which defaults to /tmp/slt.txt
ping $(slt ip)
```
