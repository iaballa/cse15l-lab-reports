# Week 3 Lab Report - Ilia Aballa

### Part 1 

Here is the code I completed to finish the week 2 lab. I've uploaded it in its entirety but will break it down later:
```
public String handleRequest(URI url){
        if(url.getPath().equals("/")){
            return String.format("Welcome to the add an item get an item webpage. To add a string, retype the url followed by /add?string=(YOUR STRING)");
        }
        else if (url.getPath().contains("/add")){
            String[] stringToAdd = url.getQuery().split("=");
            if(stringToAdd[0].equals("string")){
                stringsToDisplay.add(stringToAdd[1]);
                string.concat(stringToAdd[1]);
                return String.format("Successfully added the following string: %s", stringToAdd[1]);
            }
        }
        else if (url.getPath().contains("/search")){
            String[] stringToSearch = url.getQuery().split("=");
            for(int i = 0; i < stringsToDisplay.size(); ++i){
                if(stringsToDisplay.get(i).contains(stringToSearch[1])){
                    return String.format("%s", stringsToDisplay.get(i));
                }
            }
        }
        return String.format("Error! Either I can't do that right now, the page doesn't exist, or a typo was made somewhere. Try again!);
    }
```
    
**Breaking down the first part:**

In the first portion of this method, the user is able to add a string to the list by attaching /add?s= followed by the string they want to add. Then, if the method will split the query based on where equal signs are placed. Since there is only one, there will only be two elements that will be placed into an Array. The string at index 1 will be placed into another array called stringsToDisplay that stores all of the added strings:

```
else if (url.getPath().contains("/add")){
            String[] stringToAdd = url.getQuery().split("=");
            if(stringToAdd[0].equals("string")){
                stringsToDisplay.add(stringToAdd[1]);
                string.concat(stringToAdd[1]);
                return String.format("Successfully added the following string: %s", stringToAdd[1]);
          }
      }
 ```

**Breaking down the second part:** 

After that, the user is able to search for specific strings using /search?s= followed by the string they want to use to search.
Similar to the block above, the query is split based on the equal sign, but instead of creating an array to separate what to add, it is an array where the item at index one is the string to search for. It then iterates through stringsToAdd searching if the element contains this string, and if it does, it should print it:

```
else if (url.getPath().contains("/search")){
            String[] stringToSearch = url.getQuery().split("=");
            for(int i = 0; i < stringsToDisplay.size(); ++i){
                if(stringsToDisplay.get(i).contains(stringToSearch[1])){
                    return String.format("%s", stringsToDisplay.get(i));
                }
            }
        }
```

### The Code in Action:

The following are screenshots of the program being ran with the following input:

![](https://user-images.githubusercontent.com/114435397/195968973-38002100-4386-48d2-a29c-494fc8ce200b.png)

1. In the above screenshot, by using the path /add and query ?string=swag, I am adding swag to the list of strings. This is because the program recognizes what to do because of the /add path, and because immediately following it, the query is string=swag. So, the program knows to add the string "swag." This is because of functionality that tells the program to break the url up by / and ?.



![](https://user-images.githubusercontent.com/114435397/195968966-7523d471-ac68-4ff9-a6c2-87018221160e.png)


2. Similar to the screenshot in 1, in the above screenshot, I am adding apple to the list of strings. Again, because of the /add path followed by the string=apple query, I am able to add the string "apple." The program knows that the string should be "apple" because it is right after the question mark. The question mark allows the program to break the url up into parts it can understand and manage. 



![](https://user-images.githubusercontent.com/114435397/195968988-f7075300-8de9-4902-99a4-881b761ee6c2.png)


3. In the above screenshot, I am searching for strings that have "wag" in them. In a similar but not exact way to the two screenshots above this one, the program knows to return search results for the string "wag." In this case, the path is /search instead of add, signaling to the program that it will instead be searching instead of adding. The query in this case is s=wag, meaning that the string (s) that it will search for is "wag." The query in this case works the same, because it immediately follows a question mark, the program knows how to break the url up and how to manage each part. 

--- 

### Part 2

Here are some bugs that were in this week's lab:

**The error inducing input for this bug was:**
```
@Test
 public void testReversed1(){
   int[] input = {1, 2, 3, 4};
   assertArrayEquals(new int[]{4, 3, 2, 1}, ArrayExamples.reversed(input));
 }
```

In this test, testReversed() that is meant to test the reversed(int[] arr) function which has an integer array parameter, which it will take in, do work on, and return reversed. In this test, I give the method an integer array containing integers 1, 2, 3, and 4. The expected output is an integer array holding values 4, 3, 2, 1.

**The failure symptom:**
> 1) testReversed1(ArrayTests)
arrays first differed at element [0]; expected:<4> but was:<0>

I know the code has failed because instead of the first element of the returned array being 4, it was 0. This output is strange because there was no zero in the input, so this signals to me that something is very wrong with the program, since there are random integers where our input values should be.  

**Here is the code with the bug:**
```
static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
```


**Here is the fixed code:**
```
static int[] reversed(int[] arr) {
   int[] newArray = new int[arr.length];
   for(int i = 0; i < arr.length; i += 1) {
     newArray[i] = arr[arr.length - i - 1];
   }
   return newArray;
 }
```

The issue is that in the original reversed method, instead of returning a new array it creates, it is returning the old array instead of the new one. And within the loop that is meant to store the modified original array, the old array is the one that is being changed, not the new array. The new array has all values set to zero since that is the default for an array of int type, so within the loop, whenever arr[i] is being modified, it is always being set to zero.

--- 

### Another bug:

**Error Inducing input:**
```
@Test
 public void reverseInPlaceTest4(){
   int[] input = {-1, -2, -3, -4};
   ArrayExamples.reverseInPlace(input);
   assertArrayEquals(new int[]{-4, -3, -2, -1}, input);
 }
```
In this test, the method being tested is reverseInPlace(int[] arr). The input it is given is an integer array with values -1, -2, -3, and -4. The reverseInPlace method is supposed to change the given array instead of creating and returning a new one. So here, the expected output is the original array, just modified to hold the values -4, -3, -2, and -1.

**The failure symptom:**
> 5) reverseInPlaceTest4(ArrayTests)
arrays first differed at element [2]; expected:<-2> but was:<-3>

Based on the output, I know that something is wrong because at index 2, the expected and actual array integer values were different. Instead of -2, it was -3, signalling that something is incorrect.

**The code with the bug:**
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```

**The code with the fix:**
```
static void reverseInPlace(int[] arr) {
   int temp;
   for(int i = 0; i < arr.length/2; i += 1) {
     temp = arr[i];
     arr[i] = arr[arr.length - i - 1];
     arr[arr.length - i - 1] = temp;
   }
 }
```

The issue is that when the method is traversing the array, it is not storing the values of the indices. Instead, they are being overwritten and not saved, so when the method goes to replace the indices, it is storing the value in the last index in more places than one. (i.e. instead of the result being [4, 3, 2, 1] the result is [4, 3, 4, 4]. Once it gets to the second half of the array, the values are lost and are then incorrect. In order to fix this, there needs to be a way to stop at the “halfway” point of the array, and this can be done by dividing the length of the array by two. 











