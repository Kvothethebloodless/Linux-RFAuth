#PAM - Pluggable Authentication Module

Mechanism to integrate multiple low-level authentication schemes into a high-level API. Allows programs that rely on authentication to be written independently of the underlying authentication scheme.

#LinuxPAM

Provides dynamic authentication support for applications and services in a Linux or GNU/kFreeBSD system. Evolved from the Unix Pluggable Authentication Modules architecture. 
It is a suite of shared libraries that enable the local system administration to choose how applications authenticate users.

It's the purpose of the Linux-PAM project to separate the development of privilege granting software from the development of secure and appropriate authentication schemes. This is accomplished by providing a library of functions that an application may use to request that a user be authenticated. 

This PAM library is configured locally with a system file, **/etc/pam.conf** (or a series of configuration files located in **/etc/pam.d/**) to authenticate a user rquest via the locally available authentication modules. The modules themselves will usually be located in the directory **/lib/security** or **/lib64/security** and take the form of '**dynamically loadalbe object files**'. 
#Something about linux authentication system
In the case of traditional UNIX systems, the identity of the user is verified by the user entering a correct password. This password, after being prefixed by a two character ``salt", is encrypted (with crypt(3)). The user is then authenticated if this encrypted password is identical to the second field of the user's entry in the system password database (the /etc/passwd file). 

Privilege comes in the form of a personal user-identifier (UID) and membership of various groups. Services and applications are available based on the personal and group identity of the user. Group membership has been assigned based on entries in the /etc/group file. 
#How LinuxPAM works?
Basically LinuxPAM separates the tasks of authentication into four independent management groups:

* <u>account modules</u> - check that the specified account is a valid authentication target under current conditions. May include conditions like account expiration, time of day, and that the user has access to the requested service. 
* <u>authentication modules</u> - Verify the user's identity. e.g - requesting and checking a password or other secret. May also pass authentication information on to other system like a **keyring**.
* <u>password modules</u> - responsible for updating passwords. Generally coupled to modules employed in the authentication step. Thy may also be used to enforce strong passwords. 
* <u>session modules</u> - define actions that are performed at the beginning and end of sessions. A session starts after the user has successfully authenticated. 


#Resources
> https://en.wikipedia.org/wiki/Linux_PAM
> 
> http://www.linux-pam.org/Linux-PAM-html/sag-introduction.html
> 
> 

###Side Notes
The documentation assumes that PAM loadable object files (the modules) are to be located in the following directory: /lib/security or /lib64/security depending on the architecture. On Solaris or other implementations of UN*X, these files can be found in /usr/lib/security.