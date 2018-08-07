# USAGE

How to use this skeleton

## Customize your application

- Go to folder `src`
- Update file `appname` to set the name of your application

```bash
APPNAME=sshblock
```

- Rename the file `bashkeleton` your application's name (it is recommended to use the same name included in `APPNAME` variable).
- If your application contains configuration files, create a folder `etc` and a folder with the same name of `APPNAME` (i.e. `etc/sshblock` in this case).
- **IMPORTANT**: Update the files that implement your application in the file `INSTALL.sh`: change the content of variables `APPBASHFLATTEN`, `APPBINFILES` and `APPBASHFLATTENBINFILES`.

  - `APPBASHFLATTEN` contain the names of the files that will be "bashflattened" (i.e. their dependencies - included files using the instruction `source` - will be hard-included to get one single file without further dependencies). These files will be copied to `<PREFIX>/usr/share/$APPNAME` folder.
  - `APPFILES` contain the files that will be copied as-is to `<PREFIX>/usr/share/$APPNAME` folder.
  - `APPBINFILES` contain the names of the files that will be copied as-is to `<PREFIX>/usr/bin` folder.
  - `APPBASHFLATTENBINFILES` contain the names of the files that will be "bashflattened" (i.e. their dependencies - included files using the instruction `source` - will be hard-included to get one single file without further dependencies). These files will be copied to `<PREFIX>/usr/bin/` folder.

---
**IMPORTANT:** Have in mind that `INSTALL.sh` script will be called to INSTALL the application, using the syntax 

```console
./INSTALL.sh <src folder> <dest folder>
```

It considers the standard application structure in Linux:
- `/usr/share/appname` folder for the application
- `/etc/appname` folder for the configuration files
- `/usr/bin` folder for the standard binary applications for the users in the system.

Other structures or special considerations should be implemented.

---

## Customize the .deb package creation

- Go to folder `package/deb`.
- Edit file `create.sh`:

  - Update the values of `Depends`, `Maintainer` and `Description`.
  - Include the code of the scripts `postinst` and/or `postrm`.

---
**IMPORTANT:** Have in mind that this is a very basic script. Any complex organization or functionality should be implemented.

---

## Customize the .rpm package creation

- Go to folder `package/rpm`.
- Edit file `create.sh`:

  - Update the values of `Requires`, `Packager` and `description`.
  - Customize the appropriate sections of the created .spec file.

---
**IMPORTANT:** Have in mind that this is a very basic script. Any complex organization or functionality should be implemented.