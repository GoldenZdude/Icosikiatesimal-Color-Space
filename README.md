# Icosikiatesimal Color Space

## 7.375 × 3 = 22.125...

## 22.0 + 1.0 + 2.0 + 5.0 = 28.0...

#### Hey! That's not allowed!

### Icosik Space~!

- Ico/sik space Is a new color space I've been working on. It adresses some of the issues I have with Hex and sRGB space

  ***
  
## The issue is, given a value such as '64', its not immediately clear if this is a sRGB or HEX Color value, so in reality this value could mean... 

`100 Decimal, 64 Hexidecimal,`

`or it could mean 64 Decimal, 48 Hexadecimal,` 

`and it could even potentially mean 100 Hexadecimal, 160 sRGB, or A0 Hexadecimal.` 

This is madness! We must fix this.

# In Comes Icosik

## It would be really nice

- ### It would be really nice if we could marry sRGB and Hex Color Space so that we don't have this confusion

- #### `HEX #00A0A0 = sRGB (000, 160, 160) is not an inherently difficult thing to figure out, its just not very intuitive. I have to remember that A=10, then multiple 10*16=160. I then have to add the second part of A0, the 0. 160+0=160.

  -  Again this isnt extremely difficult, but its easy to get tripped up and forget. Base 16 is not really that intuitive to us humans, so when we see something like 2F, it may be hard to remember that the decimal conversion is (2*16)+(F=15)=2F=47.

  - It's simply very easy to get this wrong, especially if you are a child. You may think that if we have to multiply 2 by 16, you also should multiple F by 16, which would give us (2*16)+(F=15),(15*16)=272.

  - When learning to convert hexadecimal colors to sRGB colors in my head, I found myself making this mistake all the time, and even now I find myself forgetting that you dont multiply the letters by 16.

  - Icosikiatesimal Color Space attempts to make this a process a bit less demanding.

# In A World In Chaos… 


### Mama Let’s Research



#### I’m going to convert between hex colors sRGB colors and icosikaitesimal colors now I guess 



Let’s go back to our original example, #00A0A0, this is a nice teal color, about 63% intensity in the blue-green channels and 0% intensity in the red channel. 



We’ve already taken a look at how we would usually convert this to sRGB, which scales from 0-255 decimal, but let’s look at how we can convert it to... drum roll please...

## Icosik, which scales from 0-165 decimal.



First let’s separate our channels



00 Red, A0 Green, A0 Blue



I’m going to spoil that A0 is going to equal 100. Let’s see how. 



We’re going to treat A0 a bit like it’s a decimal value, and less like it’s a set of hexadecimal values. 



This is a bit like back in elementary school when we learn that to add 



`2.345 + 2.3411`



We have to make sure we line the numbers up at our decimal point so we don’t do something like 02.345 + 23.411 on accident 



Working with hexadecimal is sometimes confusing for similar reasons. One of the first things you learn when getting introduced to hexadecimal is that A means 10, B means 11, and so on, so when you you see something like A0, it looks like it should be 10 + 0 = 10, it’s not really intuitive to understand that you’re supposed to go 10*16+0=160. 



Icosik is only trying to help



It’s not without its own rules, but it still has ends up being a good margin easier. I firmly believe you could teach a five year old how to do this in half the time it would take to teach a five year old how to do it the old fashioned way. 



So let’s do it, how do we get #00A0A0 = ICO (000,100,100)?



First well just work with each channel independently 00, A0, A0 is red, green, and blue. If you already knew about hex codes before you started reading this is all just review. Since blue and green will turn out the same after conversion, let’s just focus on A0. It doesn’t really matter if we’re talking about the blue or green channel for this particular example. We separate this channel further into its first value A and its second value 0. 



Here come the fun part! Are you ready? We can assert that A is in the hundreds place as the first value of the channel, and 0 is in the ones place as the second value in the channel. This means our algorithm for conversion will have to look like this.
```
A=10 

0=0
```
Then we set up our problem so we’re working with the hundreds place as our highest place 

000 is our base

10 is our A in hundreds place 

0 is our 0 in one’s place

So it should be like this right?
```
000 base +

10[0] +

00[0] =

100
```
Or without brackets:


```
000 base +

100 +

000=

100
```


So A is still 10 and A is always 10 and you don’t have to remember anything else.

Other than `A is 10 B is 11 C is 12 D is 13 E is 14 F is 15`. 

You just have to remember that it matters what place they’re in. 

It’s simply like how 22 is equal to 20 + 2 not 2 + 2. So 0A will equal 10, and 10 will still equal 10 as well, and A0 will equal 100, because it matters if A is in the 1s place or the 100s place. 

‘A’ by itself does not equal 100, it’s still 10. 

## ‘It sounds like you’re gargling gravel’

#### I already know what you’re thinking

##### "My name is John W. Turkey and this is not how hexadecimal works. A0 hexadecimal equals 160 decimal"

#### Don't worry I have a really good comback for this

# Icosikiatesimal is not Hexadecimal, and its not decimal either.

## A0 Hexadecimal may equal 160 decimal, but A0 Icosikiatesimal equals 100 Icosikiatesimal"

It may take a moment to get over the fact that A0 looks like it could only be a hexadecimal value, but icosik is really its new thing. 

It's designed to be compatible with hex and rgb, 

So you're going to have to understand that #00A0A0 is now propery of both hex space and icosik space, and you're going to have to accept that (000, 100, 100) is now property of both sRGB space and icosik space as well.

## ‘I hate you, you're dumb for making this 1. Because icosikiatesimal means base-28 and 2. This is already worse and more convoluted than converting from hexadecimal'

Firstly wow, that's mean. :( Please be nice to me, this is my first color space I've ever created.

Secondly, the name icosikiatesimal is meaningful even though the system is not truly base-28.

Firstly, by incorporating the ABCDEF from Hex, we get parts of a base-16 system and by incoporating FF = 165 we get elements of a base-12.65 system. 16+12.65 is 28.65 so it's not like the name is meaningless.

Secondly, no way I toally dissagree that its harder! its definitely easier. lets take an example of a 'complicated' hex code like #E4DF9F. to find the RGB styled ICO values, we just seperate the channels and do the simple math that doesn't involve multiplying anything by 16
```
E4 = 

E = 14(0) +

4 = 4 == 

140 + 4= 144

similarly...

DF = 13(0) + 15 == 145

9F = 9(0) + 15 == 105

***

HEX #E4DF9F = ICO (144, 145, 105)
```

#### I already know what you’re thinking, don't you dare say it. I told you to be nice to me.

So what if we want to convert back from ICO to HEX? This is where things get fun! And where icosik really starts to show its uniqueness. We can actually parse these values back in a number of ways, such that when we convert back we actually get a new color.

(144, 145, 105)

144 can be broken down into 130 and 14 = DE instead of E4

145 can be broken down into 130 and 15 = DF the same as before

105 can be broken down into 100 and 5 = A5 instead of 9F

![My Image](https://github.com/GoldenZdude/Icosikiatesimal-Color-Space/blob/main/Destructive-Conversion-Example.png?raw=true)

# Where Love Has No Place… 

### If you say one more mean thing about "Wow this is so dumb" or "Ico can't even convert colors back correctly" im going to block you and cry. I've already asked you twice to be nice to me. 
