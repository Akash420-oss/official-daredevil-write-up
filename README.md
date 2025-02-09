DareDevil-Write-up-TryHackMe
Information
I have developed a terminal-based Reverse Engineering guessing game in C, and I've decided to deploy it to a TryHackMe room.. You can find it on my GitHub Profile.
Room
Name: DareDevil
Profile: tryhackme.com
Difficulty: Easy
Description: This room is designed to offer a game-based experience.
Author: akash420(Akash Sil)

DareDevilWrite-up
Method 1:
Download the task file - please note it may take some time as the file is a zip archive.
Download and install Oracle VirtualBox if you haven't already.
After extracting the zip file, you will find a .ovf file.

You will Find a DareDevil.ovf fileImport the DareDevil.ovf file into VirtualBox to complete the setup.

It is Importing the fileOnce the import is complete, please run the application and use the following credentials:

username: devil & password: devilAfter logging in, you should see a DareDevil icon, which is the same as the room icon.

Double-click on the icon to open it.When prompted, enter the root password: devil.
When prompted, please enter the root password: devil. After that, the window should appear as shown below.

It is showing me some rules before start the gameAfter providing my name, the window will display the following message:

It shows that I have 99 credits (or souls).It will then prompt me to spend some of the 99 souls.

I provided 0 soulNext, it will ask me to choose a level mode.

I chose Level 1: Sinister Level.After pressing Enter, the window will appear as shown below. The Devil provided a number which is 6 , and asked to specify the memory address where the number, between 1 to 5, is located.

I Entered 1Once again, the Devil requested that I give up a soul.

Again i've eneterd 0 soulAgain devil gave a number that is 85.

I entered 2Again devil said to give the number of soul.

Again i've eneterd 0 soulIt was the last lap that devil gave a number that is 49.One thing I noticed in this level is that there are certain patterns involving two stack memory addresses and three heap memory addresses. While there were no changes in the heap memory, the stack memory addresses were changing.

Then i entered 4After that I got flag of Sinister level.

After pressing the 'Got the Flag' button, I was prompted in the menu mode.

Ummm….it seems that a file was created, and I noticed that the number of souls was either decreasing or increasing..
I found i file it is located in /usr/share/dare-devil directory and the name of the file is Soul_data.txt

File looks like this:

Due to limited resources in the terminal, the font style I used is not displaying properlyHowever, if I modify the file's content, such as changing the soul value from 69 to 99, it becomes vulnerable to manipulation.

Now i gained 99 souls but don't be greedyThen, it asked me to provide the souls.

I enterd 0 SoulsAgain it asks me to select the level.

Now this time i enterd Level 2: Inferno ModeThe window appears as shown below.

Then i enterd 1Once again, I was taken to the menu mode, which indicates that there is only one lap. I also noticed that the Devil took 50 souls from me.

Now Again devil asked me how many number you want to sell??..then i provide 0 and select the inferno mode..and again played the game. But this time i got the flag of Inferno Level.

Method 2:
Now, let's approach this as a reverse engineering task - decompiling the structure of the program and analyzing the functions used within it. To do so, I am using the GNU Debugger (gdb) tool.
Again Login with credentials: username: devil & password: devil

username: devil & password: devilThen open a terminal as root user and root user password: devil
Run the command:
gdb -q dare_devil

Set the disassembly flavor to Intel by using the following command:
 set disassembly-flavor intel
Look for functions to check if any suspicious or malicious functions are defined by running:
info functions

Hmm, some of the function names appear to be malicious.Notice that system_crash function is used in this gameApart from that, I will disassemble all of the crash functions, from 1 to 8, one by one, including the systen_crash function.

It seems that i didn't load the main functionNext, load the main function, set a breakpoint, and run it. Afterward, disassemble the crash1 function, and the window will appear:

Note that there are two heap addresses in hashtag markOne thing to note is that the system function is used in this program, so it's possible that some strings are provided by this function. I will examine it further using the command:
x/s #heap_address

This Command says that delete the root directorycrash2 function:

Apart from this, it indicates that it is a recursive function, which will consume more RAM and eventually crash the system.crash3 function:

It means that kill the usercrash4 funtion:

It tells that delete the grub bootloader and shutdown itcrash5 funtion:

It means that delete the kernel file and ram file and reboot it that time due to missing kernel file & ramdisk file you can't boot itcrash6 funtion:

Thats mean you can't even use the internet the traffic is blocked. If you find it out then you can delete this rul from iptablescrash7 funtion:

According to this command whenever start the machine the machine will go for infinite loop booting processcrash8 funtion:

This funtions means that your internet interface will downsystem_crash funtion:

Ummm… time function is used..It depends on the time function, so a random value will be generated. Based on that value, the corresponding crash function will execute. It could be the crash8 function, the crash5function, or any other crash function that has been defined.

see the results….Now, I will proceed to disassemble the main functions.

lots of funtions are usedi am looking for interesting funtions….from main functions

Note Here is a function sinister_main_modeI've found a interesting funtion that is sinister_main_mode let's breakdown it.

look at the sequence of #heap_addressThe squence is again…after examine all of these i got the flag of sinister level as shown in below.

Note got the flag of Sinister levelNow again goto main function and disassble this…and look for inferno flag…

Note here is only one heap_address that is in hashtagAfter examine all of these code i got the flag of Inferno level…as shown in below.

Note Got The Inferno FlagConclusion:
Now I've got two flags:
Sinister Flag: Sinister{3v1l's Tr1umph Ach13v3d}
Inferno Flag: Inferno{Th3 H3llf1r3 St4g3 1s C0nqu3r3d}
