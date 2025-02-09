<div align="center">
<h1 color="red"> Official-DareDevil-Write-up-TryHackMe</h1>
<h2>Information</h2> 
<ul>
<li>I have developed a terminal-based Reverse Engineering guessing game in C.</li> 
<li>I've decided to deploy it to a TryHackMe room.</li>
<li>You can find it on my <a href="https://github.com/Akash420-oss/Dare-Devil">GitHub Profile.</a></li>⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
</ul>
<img  src="https://github.com/user-attachments/assets/2c2c4193-5e38-4028-b887-aadc091073a7">
</div>


## Room

- Name: DareDevil
- Profile: <a href="https://tryhackme.com/room/daredevil">tryhackme.com</a>
- Difficulty: Easy
- Description: This room is designed to offer a game-based experience.
- Author: <a href="https://tryhackme.com/p/akash420">akash420(Akash Sil)</a>

<div align="center">
  <img  src="https://github.com/user-attachments/assets/d977726b-ccdc-4820-b636-e88e82c77d43">
  <p><b>Dare Devil</b></p>
</div>


# Write-up
## Method 1:
- Download the task file - please note it may take some time as the file is a zip archive.
- Download and install Oracle VirtualBox if you haven't already.
- After extracting the zip file, you will find a .ovf file.

  <img src="https://github.com/user-attachments/assets/16f9ec99-250e-4e72-85f0-9590f0e660ba">



- You will Find a <b>DareDevil.ovf</b> file
- <b>Import the DareDevil.ovf file into VirtualBox</b> to complete the setup.

  ![image](https://github.com/user-attachments/assets/25d56b85-c862-47ad-9265-2c583ac3e2fe)


- Once the import is complete, please run the application and use the following credentials:
  - <b>username: devil
  -  password: devil</b>
    
    ![image](https://github.com/user-attachments/assets/36043681-f6ab-4308-bd52-26b1e446b827)

- After logging in, you should see a <bDareDevil icon</b>, which is the same as the room icon.

![image](https://github.com/user-attachments/assets/9449c6b9-45f2-4c3c-b474-d0e6dc99b310)


- Double-click on the icon to open it.
- When prompted, enter the <b>root password: devil.</b>
- When prompted, please enter the root password: devil. After that, the window should appear as shown below.

  ![image](https://github.com/user-attachments/assets/0ce5cb0f-1281-4022-8beb-d818afe8cb6c)

- It is showing me some rules before start the game

- After providing my name, the window will display the following message:

![image](https://github.com/user-attachments/assets/812ebf2d-7f95-46c9-bb94-f86c0e7b8dc6)

- It shows that I have 99 credits (or souls).
- It will then prompt me to spend some of the 99 souls.

  ![image](https://github.com/user-attachments/assets/eaf6fdf2-265e-43ad-8532-9aaac928d49c)

- I provided 0 soul
- Next, it will ask me to choose a level mode.

  ![image](https://github.com/user-attachments/assets/ea00612a-f48d-44ff-96bd-2336f953aa78)

- I chose <b>Level 1: Sinister Level.</b>

- After pressing Enter, the window will appear as shown below.
- The Devil provided a number which is 6 , and asked to specify the memory address where the number, between 1 to 5, is located.

  ![image](https://github.com/user-attachments/assets/c42dce14-cfe0-4291-a371-46c58bf41e76)

- I entered 1
- Once again, the Devil requested that I give up a soul.

![image](https://github.com/user-attachments/assets/037c4109-9302-4766-afdc-4c1d14ad6937)

- Again i've eneterd 0 soul
- Once more devil gave a number that is 85.

![image](https://github.com/user-attachments/assets/ad6b65f4-410a-4cf1-9d8f-e2cc955ca9ea)

- I entered 2
- Again devil said to give the number of soul.

  ![image](https://github.com/user-attachments/assets/c3538786-d0ad-46ad-b892-33b605f48ed1)

- Again i've eneterd 0 soul
- It was the last lap that devil gave a number that is 49. 
- One thing I noticed in this level is that there are certain patterns involving two stack memory addresses and three heap memory addresses.
- While there were no changes in the heap memory, the stack memory addresses were changing.

  ![image](https://github.com/user-attachments/assets/6a274986-0601-447d-8afd-2a1c7323e8a1)

- Then i entered 4
- After that I got flag of Sinister level.

![image](https://github.com/user-attachments/assets/5e1256b7-e076-43d3-8fb3-bf8e19edee07)


- While pressing the 'Got the Flag' button, I was prompted in the menu mode.

![image](https://github.com/user-attachments/assets/9c22d1e0-7e23-42b3-a134-6fbf37d0d426)


- Ummm….it seems that a file was created, and I noticed that the number of souls was either decreasing or increasing..
- I found i file it is located in /usr/share/dare-devil directory and the name of the file is Soul_data.txt

![image](https://github.com/user-attachments/assets/ecf86b91-6e2c-4166-81c6-a90e2043aeed)

- File looks like this:

![image](https://github.com/user-attachments/assets/465ebb6e-61d7-4527-bd07-c5672d90ccdf)

- Due to limited resources in the terminal, the font style I used is not displaying properly
- However, if I modify the file's content, such as changing the soul value from 69 to 99, it becomes vulnerable to manipulation.

![image](https://github.com/user-attachments/assets/4761bdd1-09e2-470c-badf-cc92a2aa842f)

- Now i gained 99 souls but don't be greedy
- Then, it asked me to provide the souls.

![image](https://github.com/user-attachments/assets/de483dfe-4782-468d-8521-276fc9939a5d)

- I enterd 0 Soul
- Again it asks me to select the level.

![image](https://github.com/user-attachments/assets/75aba008-9134-4e84-9416-0cef50d647ec)

- Now this time i enterd <b>Level 2: Inferno Mode</b>
- The window appears as shown below.

![image](https://github.com/user-attachments/assets/fdb7f019-bd47-41d4-b1ce-62f0c92aa8e7)

- Then i enterd 1
- <p>Once again, I was taken to the menu mode, which indicates that there is only one lap. I also noticed that the Devil took 50 souls from me.</p>

  ![image](https://github.com/user-attachments/assets/0dadecf5-9548-4f10-8caf-55e43d4ef869)


- <p>Now Again devil asked me how many number you want to sell??..then i provide 0 and select the inferno mode..and again played the game. But this time i got the flag of Inferno Level.</p>

![image](https://github.com/user-attachments/assets/f8268f42-1412-4c21-9642-a48841777602)


## Method 2:
- <p>Now, let's approach this as a reverse engineering task - decompiling the structure of the program and analyzing the functions used within it. To do so, I am using the GNU Debugger (gdb) tool.</p>
- Again Login with credentials:
  - username: devil
  - password: devil

![image](https://github.com/user-attachments/assets/0bb2703a-5719-493a-810c-beb55a90c39f)

- Then open a terminal as root user and <b>root user password: devil</b>
- <b>Run the command:</b>

  ```
  gdb -q dare_devil
  ```
![image](https://github.com/user-attachments/assets/19c45c3c-333d-45f5-82b9-9cfeff6f2dd6)

- <b>Set the disassembly flavor to Intel by using the following command:</b>

  ```
  set disassembly-flavor intel
  ```
- <b>Look for functions to check if any suspicious or malicious functions are defined by running:</b>

  ```
  info functions
  ```
![image](https://github.com/user-attachments/assets/8f14f18c-141d-4085-83a1-0fd60904175e)

![image](https://github.com/user-attachments/assets/ff9afeb3-0fd4-4a51-9059-685e792dbaf3)

- Hmm, some of the function names appear to be malicious.

  ![image](https://github.com/user-attachments/assets/cfdb35ba-ffc8-4693-9bbd-4c0d9437b9e6)

- Notice that system_crash function is used in this game
- <p>Apart from that, I will disassemble all of the crash functions, from 1 to 8, one by one, including the systen_crash function.</p>

![image](https://github.com/user-attachments/assets/63e2696c-3c23-4cf2-a01a-caca8c83c4df)

- It seems that i didn't load the main function
- Next, load the main function, set a breakpoint, and run it. Afterward, disassemble the crash1 function, and the window will appear:

  ![image](https://github.com/user-attachments/assets/9b376e69-e0b8-465d-978e-95956c308b31)


- Note that there are two heap addresses in hashtag mark
- One thing to note is that the system function is used in this program, so it's possible that some strings are provided by this function. I will examine it further using the command:

  ```
  x/s #heap_address
  ```
  ![image](https://github.com/user-attachments/assets/a17746f9-1153-49be-b814-a3bd5b78a514)

- This Command says that delete the root directory
- <b>crash2 function:</b>

![image](https://github.com/user-attachments/assets/966cd7cc-d501-4b62-af71-a62c8b8bdfb2)

- Apart from this, it indicates that it is a recursive function, which will consume more RAM and eventually crash the system.
- <b>crash3 function:</b>

![image](https://github.com/user-attachments/assets/9703652f-e8bd-4434-acc9-39bb94b04398)

- It means that kill the user
- <b>crash4 funtion:</b>

![image](https://github.com/user-attachments/assets/8d4e41c4-e4cc-4715-8c26-1758b7a05acb)

- It tells that delete the grub bootloader and shutdown it
- <b>crash5 funtion:</b>

![image](https://github.com/user-attachments/assets/89efcd53-7634-480e-ab24-005e4ac1a5e2)

- It means that delete the kernel file and ram file and reboot it that time due to missing kernel file & ramdisk file you can't boot it
- <b>crash6 funtion:</b>

![image](https://github.com/user-attachments/assets/cbd65aca-398c-4cec-92b3-b9269e40742b)

- Thats mean you can't even use the internet the traffic is blocked. If you find it out then you can delete this rule from iptables
- <b>crash7 funtion:</b>

![image](https://github.com/user-attachments/assets/302a3598-2951-4dc6-8b55-833e1ef3410b)

- According to this command whenever start the machine the machine will go for infinite loop booting process
- <b>crash8 funtion:</b>

![image](https://github.com/user-attachments/assets/c188d126-6ae3-4390-a059-9566970eeff4)

- This funtions means that your internet interface will down
- <b>system_crash funtion:</b>

![image](https://github.com/user-attachments/assets/3f9c49c1-ac82-4273-a3cf-fecf469169c4)

- Ummm… time function is used..
- <p><b>It depends on the time function, so a random value will be generated. Based on that value, the corresponding crash function will execute. It could be the crash8 function, the crash5function, or any other crash function that has been defined.</b></p>

![image](https://github.com/user-attachments/assets/d546d580-1fda-470e-bc28-3a0f73210f20)

- see the results….
- Now, I will proceed to disassemble the main functions.

![image](https://github.com/user-attachments/assets/61a7ad68-227e-4676-a2d6-58af88c755f6)

- lot of funtions are used

  ![image](https://github.com/user-attachments/assets/6fd1c6e5-8950-4782-971b-5c927de2b969)

- I am looking for interesting funtions….from main functions

  ![image](https://github.com/user-attachments/assets/e4574055-0b9d-4af7-8c35-8606dc538609)

- <b>Note Here is a function sinister_main_mode</b>
- I've found a interesting funtion that is <b>sinister_main_mode</b> let's breakdown it.

  ![image](https://github.com/user-attachments/assets/dd891c5b-16ab-409f-83f1-1227fef918b7)

- look at the sequence of <b>#heap_address</b>
- The squence is again…after examine all of these i got the flag of sinister level as shown in below.

![image](https://github.com/user-attachments/assets/db7d2d9e-363b-484a-8f55-ca2f4b7ccad4)

- <b>Note got the flag of Sinister level</b>
- Now again goto main function and disassble this…and look for inferno flag…

  ![image](https://github.com/user-attachments/assets/7c3cafc2-a0a3-4150-b86b-a95909614570)

- Note here is only one heap_address that is in hashtag
- After examine all of these code i got the flag of Inferno level…as shown in below.

![image](https://github.com/user-attachments/assets/e7e94205-60ea-4d1f-b7df-0620ef299032)

- <b>Note Got The Inferno Flag</b>
## Conclusion:
- Now I've got two flags:
  - Sinister Flag: <b>Sinister{3v1l's Tr1umph Ach13v3d}</b>
  - Inferno Flag: <b>Inferno{Th3 H3llf1r3 St4g3 1s C0nqu3r3d}</b>
