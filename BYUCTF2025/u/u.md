**Category** : Reverse Engineering  
**Challenge Name** : u  

**Description** :  
u  

**What was provided** :    
[u.py](https://github.com/MeDefNot/CTF-Writeups/blob/main/BYUCTF2025/u/u.py)

**Solution**  :  
  
The python code seemes gibberish at first. But, I got to one big list of integers, length of which seemed like the length of a flag.   
  
`ù=[12838,1089,16029,13761,1276,14790,2091,17199,2223,2925,17901,31599,18135,18837,3135,19071,4095,19773,4797,4085,20007,5733,20709,17005,2601,9620,3192,9724,3127,8125]`  
  
We know the flag format is `byuctf{...}`. The ASCII value of `b` is `98` and the given value of the first item of the list is `12838`. Dividing `12838` by `98` gives `131`. Similarly the ascii value of `y-u-c-t-f-{` perfectly divided the corresponding items of the list. The quotients show a pattern like  
  
`131-9-137-139-11-145-17`
  
We can see 2 and 6 are alternatively added to form two series of numbers. One starts from 131 and the other from 9. Following this approach, we could find all the quotients (a number that belongs to any one of the series and is also perfectly divides the list of integers.). So, having the quotient and dividend, we could find the divisor which is our flag.  
  
ù=[12838(131)b,1089(9)y,16029(137),13761(139),1276(11),14790(145),2091(17),17199(147),2223(19),2925(25),17901(153),31599(27),18135(155),18837(161),3135(33),19071(163),4095(35),19773(169),4797(41),4085(43),20007(171),5733(49),20709(177),17005(179),2601(51),9620(185),3192(57),9724(187),3127(59),8125(65)]  
  
`byuctf{uuuu...}`
