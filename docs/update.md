# How  to update your Orange PI

When you use Debian or Armbian ( A Debian variation build especially for ARM Devices),  updating your System via the the APT Packetmanager is easy.

#

At first u need to update the  list of repositories:

```sudo apt update ```

U have to  enter your Password, note u dont get any feedback on it, just  press enter when u entered it.
+ Standard Password for Orange Pi Images is `orangepi`

+ Standard Password for for Armbian Images is `1234`


#

After the list of repositories is updated u now can upgrade the System:

```sudo apt upgrade ```

Again u will be asked for your Password.

#

When your connection to the repository is a bit slow u can change your repositories to a location which is closer to you.  For this u have to change the  repositories in `/etc/apt/source.list`

If u want to edit this file u can use the command line editor `nano` ,

```sudo nano  /etc/apt/sources.list ```

if its not preinstalled u can install it with: `sudo apt install nano `

#

More information can be found at https://wiki.debian.org/SourcesList

U can generate a source.list convenient with this Webpage:
https://debgen.simplylinux.ch

Here u can find a guide on howto use the nano editor:
https://www.howtogeek.com/howto/42980/the-beginners-guide-to-nano-the-linux-command-line-text-editor/



