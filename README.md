# Remarkable debian package fix

For some reason the Debian package for [remarkable markdown editor](https://remarkableapp.github.io/) has not been made to install properly on Ubuntu 20.04 due to missing/outdated dependencies. There are open issues on github but nothing has been done. This repo packages the latest code into a Debian by unpacking the Debian, fixing the dependencies and copying the new code files from the Remarkable repository to the appropriate locations and then repackaging. Taking the new code is necessary to work with the new dependencies.
 
## Building the Debian package:

    git clone https://github.com/seiferteric/remarkable_debfix.git
    cd remarkable_debfix/
    dpkg-deb -Z xz -b old_deb remarkable_1.87_all.deb
    
The process was like this:

    dpkg-deb -x remarkable_1.87_all.deb old_deb
    dpkg-deb -e remarkable_1.87_all.deb old_deb/DEBIAN
    
    #... modify DEBIAN/control file
    #... copy code from main Remarkable repo into correct locations
    
    #Repackage Debian
    
    dpkg-deb -Z xz -b old_deb remarkable_1.87_all.deb
    
 
 Now you should be able to install the new debian.

## Download:

Alternatively you can download the Debian I have built [here](https://eric.seifert.casa/remarkable_1.87_all.deb)

*SHA:*

    c2c078d5a04b20ae8d89b7c40848894f946202ad  remarkable_1.87_all.deb
