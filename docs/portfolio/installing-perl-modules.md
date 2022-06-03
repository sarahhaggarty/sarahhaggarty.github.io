# Installing Perl modules

Perl is a versatile programming language that is still popular today. This article explains how to install the necessary Perl modules to run Perl scripts and functions.

A Perl module is a reusable piece of code stored in a library file. You can easily identify them by the file extension `*.pm`.

Perl modules save you time by adding functionality to your code without you having to define it from scratch. For example, if you wrote a script or function that needs to perform a series of calculations, then you can use a Perl module that already contains basic mathematical functions like addition and multiplication.

## Prerequisites
Before installing Perl modules, you need the following installed on a Linux distribution that has root permissions:
- [Perl 5](https://www.perl.org/)
- [Make](https://www.gnu.org/software/make/)
- [gcc, g++](https://gcc.gnu.org/install/)

**Optional:** [Docker](https://www.docker.com/get-started/), if you don't have a Linux distribution or you want to install modules in a separate environment.

## Find your dependencies
To find what Perl modules you need, look for any instances of `require` or `use` functions in your code.

For example:
<pre><code>require Foo;
use Bar;
</code></pre>

## Check what's installed
To check if a Perl module is installed, in a terminal, use the following command:

<pre><code> perl -e "&lt;perl-module-name&gt;;"
</code></pre>

If Perl can't find the module, you will see this response:
<pre><code> Can’t locate &lt;perl-module-name&gt;.pm in @INC
</code></pre>

`@INC` refers to the file path of libraries that Perl searches when it trys to load modules.

## Install modules using a package manager
Perl modules can be downloaded from the [Comprehensive Perl Archive Network (CPAN)](https://www.cpan.org/). To see if the Perl module you are looking for is available on CPAN, use the search on [MetaCPAN](https://metacpan.org//). If it is available on CPAN, then you can install them using package management tools such as:

- [`cpan`](https://metacpan.org/dist/CPAN/view/scripts/cpan#SYNOPSIS), which is installed by default when you install Perl.
- [`cpanm`](https://metacpan.org/dist/App-cpanminus/view/lib/App/cpanminus/fatscript.pm#SYNOPSIS), which can be installed via a terminal with the following command:
<pre><code> curl -L https://cpanmin.us | perl - App::cpanminus
</code></pre>

### Use cpan
To install modules using `cpan`, in a terminal, enter:
<pre><code> cpan &lt;perl-module-name&gt;
</code></pre>

### Use cpanm
To install modules using `cpanm`, in a terminal, enter:
<pre><code> cpanm &lt;perl-module-name&gt;
</code></pre>

## Install modules manually
To install modules manually, whether from CPAN or another source:

1. Unpack the module in a writable directory.
2. In the module directory, enter:
```
perl Makefile.PL
```
  This checks if all dependencies are installed.

{:start="3"}
3. Then enter:
```
make
make test
```
  This compiles and tests the code.

{:start="4"}
4. Then to install the module, enter:
```
make install
```

## Install modules without a Makefile
If you can't find a Makefile for the module you want to install, then you need to:

1. Make sure all dependencies are installed.
2. Add the source code for your module to a writable directory.
3. Add the directory to your Perl path by entering:
```
export PERL5LIB=<path-to-package-folder>
```

{:start="4"}
4. Check that Perl can find your module by entering:
```
perl -e "<perl-module-name>;"
```

## Note for beginners
If you are new to this topic, use Docker to test these commands. Docker containers provide a safe environment where it is easy to start again should you make a mistake. For example, this is useful when uninstalling Perl modules. Depending on your method of installation this can be difficult. You can also use Docker to build an image with the modules you need so that you can create a container only when you need it.

*Written by Sarah Haggarty*
