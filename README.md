High Level Approach:
The high level approach for this project was to create a login routine firstly in order to consistantly log into the fakebook server via HTTPS. After this was handled, all links that were found on any webpage would be added to a "frontier" in which the scraper would choose randomly which links to go to from the frontier, and then from that webpage add all links that it found to the frontier, and contiue the process until there were no links left. there would also have to be some way to keep track of websites visited, so that we would not be ping-ponging back and forth between sites, so visited sites were stored in a set as well. different status codes for each response had to be handled accordingly, which was done using a recursive method which sent a get request, and depending on the response either sent another get request (different URL for 302, same for 503) and returned the data whenever the request returned 200 OK. After this the flags would be printed out, and once the fifth flag was found the program is able to terminate

Challenges:
The first challenge that was faced was logging onto the server. The homepage had to be parsed in order to figure out exactly how the cookies were given back to the client, and also where exactly to use them. Additionally the csrfmiddlewaretoken in the HTML body of the login page was at first a mystery, and needed to be figured out how to be used. After this was completed, there was an unfortunate typo in the login code which took an entire day to find. 

The second and final challenge faced in this project was performance. At first the code was timing out on the gradescope servers, so the HTML parsing had to be optimized in order to only parse specific information from each page, and ignore others. (only attributes from h2 and a tags, etc)

Testing overview: 

most of the testing was done via remote linux machines and vms, as locally a TLS certificate error was happening. Both partners logins were used and tested in order to make sure all of the keys were able to be found. Additionally the program was allowed to run out multiple times in order to make sure that there was no infinite loop and that only 5 flags were ever being collected or printed out, ensuring that no pages were visited twice
