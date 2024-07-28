# Icosikiatesimal Color Space

## Ico space 

- Ico/sik space Is a new color space I've been working on. It adresses some of the issues I have with Hex and sRGB space

  ***
  
## The issue is, given a value such as '64', its not immediately clear if this is a sRGB or HEX Color value, so in reality this value could mean... 

`100 Decimal, 64 Hexidecimal,`

`or it could mean 64 Decimal, 48 Hexadecimal,` 

`and it could even potentially mean 100 Hexadecimal, 160 sRGB, or A0 Hexadecimal.` 

This is madness! We must fix this.

# In Comes Icosik

## It would be really nice

- It would be really nice if we could marry sRGB and Hex Color Space so that we don't have this confusion

- `HEX #00A0A0 = sRGB (000, 160, 160) is not an inherently difficult thing to figure out, its just not very intuitive. I have to remember that A=10, then multiple 10*16=160. I then have to add the second part of A0, the 0. 160+0=160.

- Again this isnt extremely difficult, but its easy to get tripped up and forget. Base 16 is not really that intuitive to us humans, so when we see something like 2F, it may be hard to remember that the decimal conversion is (2*16)+(F=15)=2F=47.

- It's simply very easy to get this wrong, especially if you are a child. You may think that if we have to Multiple 2 by 16, you also should multiple F by 16, which would give us (2*16)+(F=15),(15*16)=272.

- When learning to convert hexadecimal colors to sRGB colors in my head, I found myself making this mistake all the time, and even now I find myself forgetting that you dont multiply the letters by 16.

- Icosikiatesimal Color Space attempts to make this a process a bit less demanding.
