# Week 3 Lab Report - Ilia Aballa

**Part 1**
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
    
Breaking down the first part:
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

After that, the user is able to search for specific strings using /search?s= followed by the string they want to use to search.
Similar to the block above, the query is split based on the equal sign, but instead of creating an array to separate what to add, it is an array where the item at index one is the string to search for. I then iterates through stringsToAdd searching if the element contains this string, and if it does, it should print it:

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
Here are screenshots of it:
1) ![](https://user-images.githubusercontent.com/114435397/195968973-38002100-4386-48d2-a29c-494fc8ce200b.png)
In the above screenshot, I am adding swag to the list of strings.

2) ![](https://user-images.githubusercontent.com/114435397/195968966-7523d471-ac68-4ff9-a6c2-87018221160e.png)
In the above screenshot, I am adding apple to the list of strings. 

3) ![](https://user-images.githubusercontent.com/114435397/195968988-f7075300-8de9-4902-99a4-881b761ee6c2.png)
In the above screenshot, I am searching for strings that have "wag" in them.
