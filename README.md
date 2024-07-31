

# Icosikiatesimal Color Space

### Bit Depth per Channel = log₂(166) ≈ 7.375


### 7.375 × 3 = 22.125...

### 22.0 + 1.0 + 2.0 + 5.0 = 28.0...

###### Hey! That's not allowed!

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

Converting 8 Digit RGBA Codes 

Converting 8 digit codes (Red, Green, Blue, Alpha) from hex to Icosik follows similar steps.



First, take your code, we can use #3366abcd



Separate the channels 



33, 66, AB, CD, 



Channels without numbers simply stay as they are



33 hex = 33 ico



66 hex = 66 ico



Channels with letters have to be calculated as previously discussed 



A = 10(Tens), B = 11(Ones)

A= 100

B=11

AB= 100+11== 111



C= 12(Tens)

D=13(Ones

C=120

D=13

CD= 120+13==133



Final answer: #3366abcd = ICO (33, 66, 111, 133) 



## RGB to ICO

So we’ve talked about hex to ico and hex with alpha to ico, now let’s discuss converting directly from RGBa to ICO with RGBa values above 165.



This process sometimes results in a different answer then converting from hex, lets take a look.



Let’s take a random RGB value set such as 

(222, 200, 190)



And let’s convert it to ICO



Let’s look at our first value, 222, the value of the red channel



222/256 is .867 intensity , but we don’t want to be doing math we can’t do in our head, that was the point in the first place 



222/166 is 1.337 intensity, but that isn’t much easier than before so it doesn’t really help us.



So we’re going to do something else



Let’s take 256-222, this is easy enough to do in our heads, the answer is 34. 



Let’s take 256-200, the answer is 56.



Let’s take 256-190, the answer is 66



Then we can clip all our values above 165 to 165 and apply these values back subtracting from 165 



165-66 = 99

165-56 = 109

165-34 = 131



We can map these to our original scaled values A-B. 



222-66=131 red 

200=109 green

190=99 blue 

0.6 alpha

Then lets test by converting to hex again

131 red = 13(Tens) == (C) 
1 red = 1(Ones) == (1)

Red = C1

109 green = 10(Tens) == A
9 = 9(Ones)

Green = A9

99 Blue = 99

Final Color (222, 200, 190) = #C1A999

We can use a simple script to check out answer

```
import tkinter as tk

# Define custom conversion functions
def icosikiatesimal_to_rgb(icosik_color):
    def from_icosik(value):
        # Convert icosikiatesimal value (0-165) to RGB (0-255)
        decimal_value = int(value)
        return int(decimal_value * 255 / 165)
    
    # Extract and convert icosik components
    r = from_icosik(icosik_color['Red'])
    g = from_icosik(icosik_color['Green'])
    b = from_icosik(icosik_color['Blue'])
    
    return {
        'Red': r,
        'Green': g,
        'Blue': b
    }

def update_color():
    icosik_color = {
        'Red': red_code.get().zfill(3),
        'Green': green_code.get().zfill(3),
        'Blue': blue_code.get().zfill(3)
    }
    
    try:
        rgb_values = icosikiatesimal_to_rgb(icosik_color)
        
        # Convert to hex color
        hex_color = f"#{rgb_values['Red']:02X}{rgb_values['Green']:02X}{rgb_values['Blue']:02X}"
        
        # Update GUI components
        color_display.config(bg=hex_color)
        result_label.config(
            text=f"RGB Values: Red: {rgb_values['Red']}, Green: {rgb_values['Green']}, Blue: {rgb_values['Blue']}\n"
                 f"Hex Color: {hex_color}"
        )
    except ValueError:
        result_label.config(text="Invalid Icosik Value. Use format 000-165.")
        color_display.config(bg='white')

# Create the main window
root = tk.Tk()
root.title("Icosikiatesimal Color Viewer")

# Create and place widgets
tk.Label(root, text="Enter Icosikiatesimal Color Values (000-165):").pack()
tk.Label(root, text="Red:").pack()
red_code = tk.Entry(root)
red_code.pack()
tk.Label(root, text="Green:").pack()
green_code = tk.Entry(root)
green_code.pack()
tk.Label(root, text="Blue:").pack()
blue_code = tk.Entry(root)
blue_code.pack()

tk.Button(root, text="Update Color", command=update_color).pack()

color_display = tk.Label(root, text="Color Display", width=30, height=10, bg='white')
color_display.pack()

result_label = tk.Label(root, text="Color values will appear here.")
result_label.pack()

# Start the main loop
root.mainloop()
```
![My Image1](https://github.com/GoldenZdude/Icosikiatesimal-Color-Space/blob/main/Ico%20To%20Hex.png?raw=true)

131, 109, 99.. hmm..

Not bad, our answer #C1A999 is pretty close to #CAA899

Lets check out answers. 222, 200, 190 were our original rgb values. 
```
def rgb_to_hex(r, g, b):
    return f'#{r:02x}{g:02x}{b:02x}'

r, g, b = 222, 200, 190
hex_color = rgb_to_hex(r, g, b)
print(f'The hexadecimal color code is: {hex_color}')
```
r, g, b = 222, 200, 190 = #DEC8BE

Using our first script we can check that 

#DEC8BE = ICO 144, 128, 124

which is a good bit off from 

#C1A999 = ICO 121, 109, 99

But this is not nessessarily supposed to be seen as a problem. If you want to remain precise you can just use sRGB or HEX space, the destructive conversion is really part of the fun.

# Distribution of Colors

Total colors analyzed: 196000 ICOSIK Space Colors
```
Color Distribution:
Gray: 18.35%
Aqua: 3.54%
Navy: 4.37%
Maroon: 4.47%
Yellow: 4.03%
Silver: 14.33%
Black: 3.39%
Olive: 9.73%
Purple: 9.57%
Fuchsia: 3.56%
Lime: 3.35%
Teal: 9.49%
Blue: 3.13%
Green: 3.81%
Red: 4.26%
White: 0.61%
```

```
Total colors analyzed: 196000 HEX/RGB Space Colors

Color Distribution:
Gray: 19.67%
Silver: 17.16%
Blue: 3.46%
Aqua: 4.30%
Maroon: 3.18%
Red: 3.40%
Teal: 9.42%
Purple: 9.39%
Green: 3.21%
Olive: 9.14%
Navy: 3.02%
Yellow: 4.30%
Black: 1.64%
Lime: 3.47%
Fuchsia: 4.35%
White: 0.88%```
