# PORTSWIGGER WEB SECURITY ACADEMY

## HTTP HOST HEADER ATTACKS

### LAB : Web Cache poisoning via ambiguous requests

#### What is web Cache?
There is a web Cache present in some websites. If a particular webspage from a webserver is requested multiple times, the web server may try to keep that particular webpage in the cache memory so if other user tries to request that same page the user will get a response from the cache and load the webpage faster. The cache may store a webpage for a small amount of time.

#### What is Web Cache poisoning?
We can abuse the web cache poisoning if the server doesn't checks and validates some keys than we can try to manipulate the key parameter so that we can have our malicious resource served to the victim when the tries to get the cached webpage he will get served with the malicous code in the cached page.

#### Solution 

1. Visit to the [Portswigger website](https://portswigger.net) and login to your account.

2. The lab we are solving is [lab-host-header-web-cache-poisoning-via-ambiguous-requests](https://portswigger.net/web-security/host-header/exploiting/lab-host-header-web-cache-poisoning-via-ambiguous-requests) ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/access_web_cache_poisoning_lab.png?raw=true)

3. Access the lab and fire up your [BurpSuite](https://portswigger.net/burp/) 

4. Try to reload the page and intercept the request in the BurpSuite and send the request to the Repeater.

5. Now you see there is a HOST header in the request. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/host_header_on_the_lab.png?raw=true)

6. We can try to manipulate the Host and change it to some arbitary host.

7. We have no luck here, the site say 504 Gateway Timeout server error response.

8. We can try an easy approach, we can try to add a new Host header with an arbitary link, and now we have successfully bypassed the host header injection filter, our arbitary link is reflected in the response. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/arbitary_host_add.png?raw=true)
There is a `tracking.js` which is called from our arbitary host.

9. Now we will try to create a javascript payload in our `exploit server`. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/web_cache_piosoning_exploit_server.png?raw=true)

10. Go to your `exploit server` in the lab and set the file to `/resources/js/tracking.js` and in the body: put our desired payload i.e. `alert(document.cookie)` and save the payload. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/web_cache_piosoning_exploit.png?raw=true)

11. In the burp, add a new host with your exploit server link. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/burp_host_header_injection.png?raw=true)

12. Send the request a couple of times in the repeater so our request can be cached. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/host_header_cached.png?raw=true)

13. Now try to show the cached response in browser. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/show_request_in_browser.png?raw=true)

14. We have successfully added a javascript alert in the browser. ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/request_after_repeater.png?raw=true)

15. Voila! we have solved the lab and learned about the **HTTP HOST HEADER ATTACK** ![alt-text](https://github.com/sahildari/portswigger_web_academy/blob/main/src/web_cache_piosoning_lab.png?raw=true)
