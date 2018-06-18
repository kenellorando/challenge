# Challenge 1 Solution
1. Utilizing the first hint, replace every instance of 'X' with the number '4'. This is best achieved with either a script or command line utility.

Starting with
```
Xo 7l X1 67 Xo 7l X5 67 Xo 7l X5 ...
```

```
# with a script
function replaceX(str) {
    return str.replace(/X/g, '4');
}

# with the sed utility
sed s/X/4/g challenge.md
```

We now have
```
4o 7l 41 67 4o 7l 45 67 4o 7l 45 ...
```

2. The text looks like hexadecimal numbers, but with letters like 'l' and 'o', which do not exist in hex. The second hint of "+11" indicates a type of shift. 

Attempting a +11 caesar cipher shift on the text will yield a similar looking text but with letters towards the end of the alphabet such as "w" and "z", which are also not used in hex numbers. Logically, we should shift it in reverse and see if the resulting numbers look like real hex.

Shifting in the wrong direction:
```
4Z 7W 41 67 4Z 7W 45 67 4Z 7W 45 ...
```

Using a -11 shift will produce the correct text, one whose letters range alphabetically from A-F.
```
4D 7A 41 67 4D 7A 45 67 4D 7A 45 ...
```

3. Now we have real numbers to work with. Running the resulting string in a hex to ASCII converter will produce a strange text starting with
```
MzAgMzEgMzEgMzAgMzEgMzAgMzAgMz ...
```
This text is also designed to confuse. Though it resembles nothing but nonsense ASCII, it is actually base64 encoded. Running the text through a base64 to ASCII converter should produce a string of numbers, also resembling hex.
```
30 31 31 30 31 30 30 30 20 30 31 31 ...
```

4. We're home free. Convert the hex to ASCII again and the resulting text is binary.
```
01101000 01110100 01110100 01110000 01110011 00111010 ...
```

5. Convert the binary to ASCII and enjoy your prize!
