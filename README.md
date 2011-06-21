# pwgen - generate pronounceable passwords

## About

I am the well known password generator pwgen. You can read more about me on my [manual page][].

## How did I get here on GitHub?

[Philipp][] took my sources from the [sourceforge project site][] and republished me as a Git
repository here on GibHub.

To get there, he downloaded the .tar.gz packages from the download section of the project on sf.net.
A `git cvsimport` was not possible as newer versions were not checked-in to CVS on SF.net.
To automatically create the repository, he used the following Bash Script:

    #!/bin/bash
    
    for version in 2.0 2.01 2.02 2.03 2.04 2.05 2.06
    do
        wget http://sourceforge.net/projects/pwgen/files/pwgen/$version/pwgen-$version.tar.gz/download
    done
    
    mkdir pwgen
    cd pwgen
    git init
    cd ..
    
    for archive in $(ls pwgen*tar.gz)
    do
        tar -xf $archive
        cd pwgen; git rm -rf *; cd ..
        archive_dir=$(basename $archive .tar.gz)
        mv $archive_dir/* pwgen/
        cd pwgen; git add .; git commit -m "automatic commit for $archive_dir"; cd ..
        rm -rf $archive_dir
    done

## Issues

For an overview over the current status on Debian & Ubuntu have a look at the 
Debian package tracking system (including information about bugs etc):
<http://packages.qa.debian.org/p/pwgen.html>.
Also helpful: [Ubuntu's Bugtracker for pwgen](https://bugs.launchpad.net/ubuntu/+source/pwgen/).

## The author

* Theodore Ts'o <tytso@alum.mit.edu>  
  Modelled after a program originally written by Brandon S. Allbery, and then later extensively modified by Olaf Titz, Jim Lynch, and others.

[manual page]: http://linux.die.net/man/1/pwgen
[sourceforge project site]: http://sourceforge.net/projects/pwgen
[Philipp]: https://github.com/pklaus

## Ports to Other Lanugages and Alternatives

* For MS Windows there is [PWGen for Windows](http://pwgen-win.sourceforge.net/).
* There is a port to PHP: [pwgen-php](http://code.google.com/p/pwgen-php/)
* and to Javascript: <http://8-p.info/pwgen/>.
* An alternative with easier to remember passwords: [gpw](http://www.multicians.org/thvv/gpw.html) which is a Trigraph Password Generator written in Java (also available in C/C++ and Javascript)
* Here is a [discussion of tools for the generaton of memorable passwords](http://superuser.com/questions/237228/linux-tool-to-generate-memorable-passwords).
