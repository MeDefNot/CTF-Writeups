### Category : Miscellaneous  
### Challenge Name : Conway's Pattern  

     
### Description :  
I think i went a generation ahead  

### What was provided :    
[chall.rle](https://github.com/MeDefNot/CTF-Writeups/blob/main/DVCTF2025/Conway's-Pattern/chall.rle)

## Solution  :  

  
First off,
## What is ".rle"?  
  
The .rle file extension typically stands for Run-Length Encoded file. This is a simple form of lossless data compression where consecutive repeated values (runs) are stored as a single data value and a count, instead of the original run

**What's inside?**  
After some research i found that the file contains positions for `Conway's game of life`. `x = 840, y = 7` means the grid is 840 squares in width and 7 squares n height. And '2b' means '2 dead cells' , '2o` means '2 alive cells`. `$` means a new line and so on.  

  
## Conway's Game of Life Overview  
    
It's a grid-based simulation where each cell is either alive or dead. The grid updates in steps called generations. Each cell looks at its 8 neighbors to decide what happens next.

**Rules**  
For each cell:

For a cell that is currently alive:

* Survival: If it has 2 or 3 live neighbors, it stays alive.

* Underpopulation: If it has fewer than 2 live neighbors, it dies.

* Overpopulation: If it has more than 3 live neighbors, it dies.

For a cell that is currently dead:

* Reproduction: If it has exactly 3 live neighbors, it becomes alive.


After meticulously searching for an online viewer.I finally found ![Golly](https://golly.sourceforge.io/webapp/golly.html). The code looks like,  
.  
  
![image](https://github.com/user-attachments/assets/b1c925d3-3874-4f98-bd61-8a5ed20f92e4)  
.  

Close-up view  
.  

![image](https://github.com/user-attachments/assets/9f42f30c-0d26-4ea4-8278-7b229d905675)  
.  


As the challenge implies, this is a generation ahead of the given flag. WHich means we need to backtrack from here.  

i noticed theres distinctly these blocks along with straight lines that go horizontally and nothing else  
![image](https://github.com/user-attachments/assets/0585d4c8-0907-4ee9-af57-a406d4844673)  

SO, these cannot be seperate letters, as that would give different patterns in the entire image. I speculated this may be zero(0). And what if the surrounding straight lines are ones(1)?
This would mean the beginning is,
![image](https://github.com/user-attachments/assets/ffc5a20f-b069-4612-b438-bd042b52ad60)
 .  
 
If 0100010 is a binary number, it's decimal would be 68.... ASCII value of 'D'! The first character of flag format `DVCTF{}`  


Continueing in this way, I could extract the following binary:  

`01000100 01010110 01000011 01010100 01000110  01111011 01000011 00110000 01101110 01110111 00110100  01011001 01011111 01000010  00110001 01101110 00110100 01110010 01111001 01111101`  

Which reads `DVCTF{C0nw4Y_B1n4ry}`


