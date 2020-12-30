# REFLECTED CROSS SITE SCRIPTING

## Lab: Reflected XSS into HTML context with nothing encoded

This is a very simple cross site scripting lab, in this particular website our most basic cross site scripting payload will get executed.

The lab descrption says, we just have to call the alert function in order to solve the lab.

## Solution

1. Access the [lab](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/01_basic_rxss_lab.png?raw=true)

2. On the lab we will be seeing the search bar, here we can try to search something.(say rxss)

![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/01_basic_rxss_search.png?raw=true)

3. Our search query gets reflected on the webpage(in the html document) and the url itself.

![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/01_basic_rxss_reflection.png?raw=true)

4. Now we can try to perform Reflected Cross Site Scripting Attack using a basic alert script `<script>alert('rxss')</script>`.

![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/01_basic_rxss_alert_script.png?raw=true)

5. We have successfully generated an alert on the website and now our lab is solved.

![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/01_basic_rxss_lab_solved.png?raw=true)
