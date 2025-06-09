-----
# Linux File Permissions
----

## 1\. Permission Classes

| Class | Abbreviation | Description |
| :------ | :-------- | :-------------------------------------- |
| **User** | `u` | Owner of the file or directory. |
| **Group** | `g` | Members of the group that can access. |
| **Other** | `o` | Other users on the system (not the owner or group members). |
| **All** | `a` | All users (User, Group, and Other). |

----

## 2\. Permission Representation

Each permission type has a symbol and a numeric (octal) value:

| Permission | Symbol | Numeric Value | Description |
| :-------- | :----- | :------------ | :------------------------------------------ |
| **Read** | `r` | `4` | Can view file contents or list directory contents. |
| **Write** | `w` | `2` | Can modify/delete files or create/delete items in directories. |
| **Execute** | `x` | `1` | Can run files or enter directories. |
| **None** | `-` | `0` | No permission. |

### Numeric (Octal) Permissions

Combine the numeric values ​​for each class (User, Group, Other).

* `rwx` = $4 + 2 + 1 = \\textbf{7}$
* `rw-` = $4 + 2 + 0 = \\textbf{6}$
* `r-x` = $4 + 0 + 1 = \\textbf{5}$
* `r--` = $4 + 0 + 0 = \\textbf{4}$
* `---` = $0 + 0 + 0 = \\textbf{0}$

**Common Example:**

| Numeric Permissions | Symbolic Permissions | Description |
| :----------- | :------------ | :------------------------------------- |
| `755` | `rwxr-xr-x` | Owner: read/write/execute. Group & Others: read/execute. |
| `644` | `rw-r--r--` | Owner: read/write. Group & Others: read only. |
| `700` | `rwx------` | Only owner can read/write/execute. |
| `600` | `rw-------` | Only owner can read/write. |

-----

## 3\. Viewing File Permissions

Use the `ls` command with the following options:

* **`ls -l`**: Displays a long list, including permissions.
* **`ls -la`**: Displays a long list, including hidden files.

**Example Output:**

```bash
$ ls -l
-rw-r--r-- 1 user group 1024 Apr 1 09:00 myfile.txt
drwxr-xr-x 2 user group 4096 Apr 1 10:00 mydirectory/
```

**Permission Line Explanation (Example: `-rw-r--r--`):**

1. **First Character (`-` or `d`):** Indicates the file type (`-` for files, `d` for directories).
2. **Next 3 Characters (`rw-`):** Permissions for **Owner**.
3. **Next 3 Characters (`r--`):** Permissions for **Group**.
4. **Last 3 Characters (`r--`):** Permissions for **Other**.

-----

## 4\. Commands to Change Permissions

### `chmod` (Change Mode)

Change the permissions of a file or directory.

* **Symbolic Syntax:** `chmod [who][+/-/=][permissions] [file/directory]`
* **Example:** `chmod u+x myscript.sh` (add execute permission for owner)
* **Example:** `chmod go -w mydoc.txt` (remove write permission for group and others)
* **Example:** `chmod a=r myconfig.conf` (set all to read only permissions)
* **Numeric Syntax:** `chmod [3-digit number] [file/directory]`
* **Example:** `chmod 755 myscript.sh` (gives `rwxr-xr-x`)
* **Example:** `chmod 644 mydata.txt` (gives `rw-r--r--`)

-----

### `chown` (Change Owner)

Change the owner of a file or directory (requires `sudo` privileges).

* **Syntax:** `chown [new_owner] [file/directory]`
* **Example:** `sudo chown john myfile.txt`
* **Changing Owner and Group:** `chown [new_owner]:[new_group] [file/directory]`
* **Example:** `sudo chown mary:developers myapp/`

-----

### `chgrp` (Change Group)

Change the group of a file or directory (requires `sudo` privileges).

* **Syntax:** `chgrp [new_group] [file/directory]`
* **Example:** `sudo chgrp sales report.pdf`

-----

## 5\. Special Permissions

These are advanced permits
