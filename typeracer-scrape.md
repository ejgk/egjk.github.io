---
title: Document Center
---

## How to scrape text from TypeRacer

* Open TypeRacer normally while open the inspector
* Load a text
* Note that there's a request to `https://play.typeracer.com/gameserv` etc.
* Right click at the request and choose "copy as curl".
* Run it in a loop.

## How to parse the fetched data:

* Note that the data looks like JavaScript.
* Use the code

    ```
    node -e "
         var a=eval(String.raw`$(tail -c+5 o)`);
         var s=a.slice(-3)[0].slice(-3)[0];
         assert(s.length>15);
         console.log(s);"
    ```

    to parse the output (the assert is used to make sure that the fetched entry is the correct one,
    assume the output of curl is stored in file `o`)

## Session ID?

The command `curl 'https://play.typeracer.com' | grep -Po '(?&lt;=jsessionid=)\w*' | tee sessionid`
can be used to get the session ID and also store it to the file named `sessionid`.
