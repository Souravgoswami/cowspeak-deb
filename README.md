# Cowspeak Deb 🐮
Moved to
https://github.com/Souravgoswami/cowspeak-root/

https://souravgoswami.github.io/cowspeak/

Display a gradient colourful animal with a random quote or your own text in your terminal.

![cowspeak](https://github.com/Souravgoswami/cowspeak-deb/blob/master/Screenshots/Screenshot_2019-01-24_23-10-28.png)

---

It depends on `ruby`. Cowspeak recommends you to use `Ruby 2.4.0+`.

Note that this is only for GNU/Linux systems. [Here's another cowspeak repository](https://github.com/Souravgoswami/cowspeak) that can be run locally without any root permission.

Cowspeak Debian installer can also be found [here](https://www.opendesktop.org/p/1271477/).

---

## Running Cowspeak on Debian/Linux Mint/Ubuntu/Kali Linux/Raspbian/Other Debian Based Systems 🐄

   + Download the latest deb file ![from here](https://github.com/Souravgoswami/cowspeak-deb).
        
   + Install the deb file:
            `dpkg -i cowspeak-v<version>.deb`
                Or
             You can use gdebi-gtk.

## Running Cowspeak on Other Linux Distributions ⚙️

If you want to run `cowspeak` in Arch Linux / OpenSUSE / Fedora / CentOS / RedHat etc. other GNU/Linux distributions, then please follow the steps:
    
   + Make sure you have **Ruby** 💎:
   
         A. Arch Linux 🏹 : `sudo pacman -S ruby`
         
         B. Fedora / CentOS: `sudo yum install ruby`
         
         For any other distribution, install the Ruby package. When done, follow the next step!

   + Run the ![Root_Installer.rb](https://github.com/Souravgoswami/cowspeak-deb/blob/master/Root_Installer.rb) as root.
         
        Example: `sudo ruby Root_Installer.rb`
         
        Press Enter to Confirm each step.

   + When the above step succeeds, run:
        `sudo cowspeak -dl`
   
## 🐮 Cowspeak Accept Arguments. All the Available Arguments are 👇
```
1         --art or -a                   Display a tutorial on adding your own art.
2         --blink or -b                 Blink the texts.
3         --borderh=<ch>/-brh=<ch>      Horizontal border character.
4         --borderv=<ch>/-brv=<ch>      Vertical border character.
5         --bubble=<text>/-bbl=<text>   Specify the character of speech balloons.
6         --documentation/-d            Display the documentation.
7         --download/-dl                Download missing files from Github.
8         --file=<path>/-f=<path>       Specify the path of your own ASCII art.
9         --fill=<char>/-fc=<char>      Fill the quote area with a character.
10        --force-update/-fu            Forcefully update (also see --update)
11        --help/-h                     Display help.
12        --invert/-inv                 Invert the output (right <- left in English)!
13        --manual/-m                   Display a manual. Same as documentation.
14        --net=<url>/-n=<url>          Read data from a website (in curl format).
15        --no-art/-na                  Don't display the animal.
16        --no-colour/-nc               Don't colourize the output.
17        --no-text/-nt                 Don't show any text, show the animal.
18        --read=<file>/-r=<file>       Read a file.
19        --reverse/-rev                Cowspeak reads upside down!
20        --rotate-colour/-rc           Rotate the output colours in each line.
21        --show-arts/-sa               Show arts in the default directory.
22        --text=<text>/-t=<text>       Display a custom text.
23        --version/-v                  Display the current /usr/bin/cowspeak version.
24        --update/-u                   Update cowspeak if possible.
25        --welcome/-w                  Show some system details to the user.
```

## Note on Arguments 📝
You have to pass each argument separately. For example, cowspeak -rc rotates the colour of the output, and -w shows a welcome screen with some system status and information. So if you want to use both, you have to use cowspeak -rc -w (instead of cowspeak -rcw).

If you pass an invalid argument, cowspeak will not inform you. It will simply ignore the invalid argument so you can cheer!

## Screenshots 📸
![alt cowspeak --welcome](https://github.com/Souravgoswami/cowspeak/blob/master/Screenshots/b.png)
 
![cowspeak](https://github.com/Souravgoswami/cowspeak-deb/blob/master/Screenshots/Screenshot_2019-03-26_04-04-36.png)
 
![cowspeak](https://github.com/Souravgoswami/cowspeak-deb/blob/master/Screenshots/Screenshot_2019-03-26_04-04-11.png)

## Bug Report 🐞
Cowspeak considers bugs and security issues very seriously 🐛. If you got any bug in cowspeak, any security issue, or an idea, please let me know via [GitHub](https://github.com/Souravgoswami/cowspeak-deb/issues/new) or email me souravgoswami@protonmail.com
