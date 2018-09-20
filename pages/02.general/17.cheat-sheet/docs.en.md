---
title: 'Cheat-sheet'
taxonomy:
    category:
        - docs
visible: false
---


 This is a cheat sheet that explains how to easily manage blocking rules and elements to hide. More detailed information you can find in this [article](https://kb.adguard.com/en/general/how-to-create-your-own-ad-filters)

### Tools you might need

An irreplaceable tool to work primarily is the browser, the best way to do this is to use Google Chrome / Canary / Firefox and Dev Tools, which are built into them.

* Browser Developer Tools ([Chrome](https://www.google.com/chrome/?), [Firefox](https://www.mozilla.org/ru/firefox/new/), [Edge](https://support.microsoft.com/ru-ru/help/4027741/windows-get-microsoft-edge), [Safari](https://www.apple.com/ru/safari/))
* AdGuard Filtering Log

## Comments

For additional explanation you should use this exclamation point "!" at the beginning of the rule that indicates a comment.

* ! Don't mind if I do - is a comment.

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Comment.PNG" width="700">

## Options in blocking rules

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Options%20in%20blocking%20rules.png" width="750">

* ||ads.example.com^$script,image,domain=example.com|~boo.example.info is a rule parts

* || — Matching the beginning of an address. http://, https://, ws://, wss:// at once

* ads.example.com — Verbatim text. This text must be present in the address to be blocked

* ^ — Separator. The address must either end here or a separator character like ? or / has to follow

* $ — option separator. This character indicates that the following text defines filter option

* script, image — Restriction by content type. Type options define request types to be blocked

* domain — Domain option. Limits the rule application area to a list of domains (and their subdomains)


## Basic rules

The most simple rules are so-called "Basic rules". They are used to block requests to specific URLs. Or to unblock it, if there is a special marker "@@" at the beginning of the rule. The basic principle for this type of rules is quite simple: you have to specify the address and additional parameters that limit or expand the scope of the rule.

### Blocking by domain name


The basic rules are designed to block unwanted sites on their own or add an exception. Let's do an example:

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Blocking%20by%20domain%20name.PNG" width="750">

This rule blocks:

http://ads.example.com/foo.gif

http://server1.ads.example.com/foo.gif

https://ads.example.com:8000/

This rule doesn't block:
										
http://ads.example.com.ua/foo.gif

http://example.com/redirect/http://ads.example.com/	


## Blocking by address parts

 <img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Address%20parts.png" width="750">

This rule blocks:

 http://example.com/banner/ads/img

 http://example.com/banner/ads/bar/img?param

 http://example.com/banner/img/ad1 



This rule doesn't block:

http://example.com/banner/img

http://example.com/banner/ads/imgraph

http://example.com/banner/ads/img.gif

### Unblocking particular requests

@@||example.org/banner

This is a basic exception rules that should guide you to understand the regularity and principles of exceptions.

Example 1: Exception for particular requests

@@||ads.example.com/notbanner^$~script

Rule parts

* @@ — Exception marker. Rules starting like this are exceptions, they will override blocking rules;

* || — Matching the beginning of an address. http://, https://, ws://, wss:// at once;

* ads.example.com/notbanner — Verbatim text. This text must be present in the address to be blocked;

* ^ — Separator. The address must either end here or a separator character like ? or / has to follow;

* $ — option separator. This character indicates that the following text defines filter option;

* ~script — Restriction by content type. This type option prevents the exception from being applied to scripts.
													
----------------- ----------------- ----------------- ----------------- 

----------------- ----------------- ----------------- ----------------- 

## [Cosmetic rules](https://kb.adguard.com/general/how-to-create-your-own-ad-filters#cosmetic-rules-1)


As the name suggests, cosmetic rules are used not for blocking ad requests, but for changing the page appearance. They can hide the elements or even convert the overall style of pages.

Work with cosmetic rules requires the basic knowledge of HTML and CSS. So, if you want to learn how to make such rules, we recommend to get acquainted with this [documentation](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors).


### Element hiding

 Sometimes you will find advertisements that can't be blocked because they are embedded as text in the web page itself. If you look at the source code of the web page you might find something like this:
 
<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/%23%23.png" width="750">

  
  

   Selector | Description
------------ | -------------
##banner | Matches the element with the unique id `banner`: ![example domain 2017-06-14 11-34-20](https://user-images.githubusercontent.com/5947035/27123120-8b07e058-50f5-11e7-85a0-862d8f8b45e5.png)
.banner | Matches all elements with class `banner`:  ![example domain 2017-06-14 11-33-30](https://user-images.githubusercontent.com/5947035/27123139-9ca6ce6e-50f5-11e7-804b-1891953bf668.png)




    * Example 1: Element hiding rule for a particular domain
`example.com##div[class="adverts"]`

    * Example 2: Element hiding exception rule
`example.com#@#div[class="adverts"]`

    * Example 3: CSS rule
       * Remove backgroung image:
`example.com#$#body { background: none!important; }`

       * Change element height for avoid primitive ad blocking detection:
`example.com#$#div[id^="ad_"] { height: 1px!important; }`


### Frequently used selectors

Table with examples of the following selectors:

* class (
* id
* tag name
* attribute selectors



</details>

>


