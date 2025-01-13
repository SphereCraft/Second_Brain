
# Notes / Work - 13-01-2025

### 📅 Date: 13-01-2025
### 🕒 Time: 09:39:18

# Password Manager

Using the Linux based password manager - Password Store
    Some key commands:
        to get started need to generate a gpg key - run --gen-key to generate a key
        then add your details and remember the main password, never lose this.
        gpg -K to retrieve your key
        gpg --list-keys to list all keys
        gpg --edit-key <key id> to edit your key
        gpg --delete-key <key id> to delete your key

    To add a new password:
        pass insert <name of password>
        pass edit <name of password>
    To copy first line of password to clipboard:
        pass show -c <name of password>

    To delete a password:
        pass rm <name of password>
    to undelete a password:
        pass undo <name of password>

    To list all passwords:
        pass
        pass ls
        pass list
        pass show
        pass grep

    pass init with the key to initialise the password store
    pass git-init to initialise the password store in git
    pass git-add to add the password store to git
    pass git-push to push the password store to git
    pass git-pull to pull the password store from git

    To generate a new password:
        pass generate <name of password>
        pass generate --length <length of password>

    To generate a new password in a particular directory and file:
        pass generate directory_path/file_name

    to view password directory tree:
        pass tree
        or pass to show all passwords

    to view passwords
        pass show <name of password>
         
    to edit passwords
         pass edit <name of password>
         pass edit --force <name of password>
         pass edit --multi <name of password>
         pass edit --multi --force <name of password>







---

## References

