# Tweeter Unfollow [Javascript]
A very simple and efficient script that will dynamically delete all your tweeter subscriptions at the desired speed.

# Usage
Just go to the URL text box, write "javascript:" and paste all the script (Ctrl + V) then press Enter.
The script will ask you the delay between two unfollow (usage of "1000" or "500" is recommended)

# Example
**Don't forget to change the variables FOLLOW_TEXT and UNFOLLOW_TEXT according to your language (French is used here)** 
```Javascript
var FOLLOW_TEXT = "Abonné";
var UNFOLLOW_TEXT = "Se désabonner";
```

Example of usage in the URL Barre:
```
javascript:var FOLLOW_TEXT = "Abonné"; var UNFOLLOW_TEXT = "Se désabonner"; function search(){ var v = document.getElementsByTagName("*"); for(var i = 0; i < v.length; i++) { if(v[i].innerText == FOLLOW_TEXT && v[i].attributes[0].value == "button") { v[i].click(); unfollow(); var temp = getMaxParent(v[i]).parentElement.parentElement; temp.style.transitionDuration = "0.3s"; temp.style.height = 0; temp.style.opacity = 0; return; } } } function getMaxParent(id) { var elem = id; do { elem = elem.parentElement; } while (elem.attributes[0].value != "button"); return elem; } function unfollow(){ var v = document.getElementsByTagName("*"); for(var i = 0; i < v.length; i++) { if(v[i].innerText == UNFOLLOW_TEXT) { v[i].click(); return; } } } setInterval(search, parseInt(prompt("Delay:", 1000)));
```
**Warning: Don't forget the "javascript:" at the beginning**. *(This one is removed from the press by Chrome.)*

# Script
## Search Function
Main function of the script, this one will detect the first valid "Followed user", next it will click on it call UnFollow Function, then the GetMaxParent Function that will return the container of the concerned user to hide him.

```Javascript
function search(){
    var v = document.getElementsByTagName("*");

    for(var i = 0; i < v.length; i++) {

        if(v[i].innerText == FOLLOW_TEXT && v[i].attributes[0].value == "button") {
            v[i].click();
            unfollow();
            
            var temp = getMaxParent(v[i]).parentElement.parentElement;

            temp.style.transitionDuration = "0.3s";
            temp.style.height = 0; 
            temp.style.opacity = 0;

            return;
        }
    }
}
```

## UnFollow Function
UnFollow function will detect the button to confirm the unfollow and click on him.

```JavaScript
function unfollow(){
    var v = document.getElementsByTagName("*");

    for(var i = 0; i < v.length; i++) {
        if(v[i].innerText == UNFOLLOW_TEXT) {
            v[i].click();
            return;
        }
    }
}
```
## GetMaxParent Function
One function totally esthetic that will return the HTML Element that contain unfollowed user to apply an animation into Search Function

```Javascript
function getMaxParent(id) {
    var elem = id;
    do {
        elem = elem.parentElement;    
    } while (elem.attributes[0].value != "button");
    return elem;
}
```

## Simple Interval 
Here is a simple interval script, it will ask the delay before two unfollow.

```Javascript
setInterval(search, parseInt(prompt("Délais de suppression:", 1000)));
```


# Full Code
```Javascript
var FOLLOW_TEXT = "Abonné";
var UNFOLLOW_TEXT = "Se désabonner";

function search(){
    var v = document.getElementsByTagName("*");

    for(var i = 0; i < v.length; i++) {

        if(v[i].innerText == FOLLOW_TEXT && v[i].attributes[0].value == "button") {
            v[i].click();
            unfollow();
            
            var temp = getMaxParent(v[i]).parentElement.parentElement;

            temp.style.transitionDuration = "0.3s";
            temp.style.height = 0; 
            temp.style.opacity = 0;

            return;
        }
    }
}

function getMaxParent(id) {
    var elem = id;
    do {
        elem = elem.parentElement;    
    } while (elem.attributes[0].value != "button");
    return elem;
}

function unfollow(){
    var v = document.getElementsByTagName("*");

    for(var i = 0; i < v.length; i++) {
        if(v[i].innerText == UNFOLLOW_TEXT) {
            v[i].click();
            return;
        }
    }
}

setInterval(search, parseInt(prompt("Délais de suppression:", 1000)));
```
