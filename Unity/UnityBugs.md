# Some magic bugs in Unity(C#)

## A Script Attached to an Object will Automatically Have a Member Variable "name"
I was using a string parameter passed from outside called "itemName" in a function, while I made a mistake that "itemName" was wrotten as "name". Astonishingly, it didn't report any bug at right here until a bug arose at another part, where I using this string variable as a key of a dictionary. After a investigation, I found that the "name" is just the name of that GameObject listed in the Unity Scene (on the left).

