# GRUB-themes

This repository was created to create and store my GRUB 2 themes.

# Rules of the repository

Repo consists of:
- README.md - this file
- .gitignore file - normal gitignore
- themes folder - folder storing themes. Each theme has its own folder with it`s theme.txt but also fonts(.pf2), pictures(.png) and README.md with info about theme, sources of resources like images, for what resolution theme was made etc.
- grub.cfg - custom grub.cfg file needed by some tools to properly preview theme.
- grubenv - grub environment file to persist some values between boots. Needed by grub.cfg .

# Making themes

GRUB2 documentation for creating themes can be found:
- [here][GRUB_DOC].
- [tutorial_here][GRUB_THEME_TUTORIAL] (ROSA linux doc)
- [help_to_tutorial][additional_doc] (ROSA linux doc)

Creating themes user should be aware of facts that:
- There is very little amount of tutorials and documentation. Moreover, in many cases documentation is missing some parameters (situation on 08.2024)
- Fonts used by GRUB are in .pf2 format. To use font user should provide name of font not a file name. [Here][PF2_checker] is online tool to check it.
- Do not use element: canvas. It causes bad behavior for elements that it contain.
- Try to use as little hbox and vbox as possible, they also cause some problems.

**Important**- Remember to add README.md to every theme with info about theme, sources of resources like images, for what resolution theme was made etc.

## Making themes for Arch

To create theme for Arch Linux user needs:
- some software for file editing like nano, vim or vscode
- special package available on AUR called grub2-theme-preview ([github][GITHUB_grub2-theme-preview] , [AUR_website][AUR_grub2-theme-preview])

Next user needs to create theme folder and theme.txt with it using [documentation][GRUB_DOC], adding imiges and fonts.

To preview theme user should use grub2-theme-preview with this parameters:
```
grub2-theme-preview --grub-cfg ./grub.cfg --verbose ./themes/manjaro
```
- **--grub-cfg ./grub.cfg** - this parameter points out to custom grub.cfg file. Otherwise command would try to access real grub.cfg file in /boot/grub/grub.cfg .
- **--verbose** help to resolve problems.
- **./themes/manjaro** thats a path to theme folder.

After running this command window with virtual machine will pop up presenting the theme.

**Warning** grub2-theme-preview does not work for **VS code** from snap(try to run it from console) and because it uses **kvm** there cannot be any other running virtual machines(more [here][KVM_and_VBox]).

### Resolution

User in grub.cfg file in this repo can set up his resolution. It is first line:
```
set gfxmode=auto
```
Value auto is default, User can set up his own f.e:
```
 set gfxmode=1920x1080
```


[GRUB_DOC]: https://www.gnu.org/software/grub/manual/grub/grub.html#Theme-file-format
[GRUB_THEME_TUTORIAL]: http://wiki.rosalab.ru/en/index.php/Grub2_theme_tutorial
[additional_doc]: http://wiki.rosalab.ru/en/index.php/Grub2_theme_/_reference
[PF2_checker]: https://filext.com/online-file-viewer.html
[GITHUB_grub2-theme-preview]: https://github.com/hartwork/grub2-theme-preview
[AUR_grub2-theme-preview]: https://aur.archlinux.org/packages/grub2-theme-preview
[KVM_and_VBox]: https://askubuntu.com/questions/413511/can-virtualbox-and-kvm-run-alongside-each-other