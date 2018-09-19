---
title: 'Cheat-sheet'
taxonomy:
    category:
        - docs
visible: false
---


 This is a cheat sheet that explains how to easily manage blocking rules and elements to hide. More detailed information you can find in this [article](https://kb.adguard.com/en/general/how-to-create-your-own-ad-filters)

## Blocking by address parts

! Intro next

 <img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Address%20parts.png" width="750">

This rule blocks:

 http://example.com/banner/ads/img

 http://example.com/banner/ads/bar/img?param

 http://example.com/banner/img/ad1 



This rule doesn't block:

http://example.com/banner/img

http://example.com/banner/ads/imgraph

http://example.com/banner/ads/img.gif


----------------- ----------------- ----------------- ----------------- 



## Blocking by a domain name

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Blocking%20by%20domain%20name.PNG" width="750">

This rule blocks:

http://ads.example.com/foo.gif

http://server1.ads.example.com/foo.gif

https://ads.example.com:8000/

This rule doesn't block:
										
http://ads.example.com.ua/foo.gif

http://example.com/redirect/http://ads.example.com/	


## Basic exception rules

This is a basic exception rules that should guide you to understand the regularity and principles of exceptions.

Example 1: Exception for particular requests

@@||ads.example.com/notbanner^$~script

Rule parts

@@ — Exception marker. Rules starting like this are exceptions, they will override blocking rules;

|| — Matching the beginning of an address. http://, https://, ws://, wss:// at once;

ads.example.com/notbanner — Verbatim text. This text must be present in the address to be blocked;

^ — Separator. The address must either end here or a separator character like ? or / has to follow;

$ — option separator. This character indicates that the following text defines filter option;

~script — Restriction by content type. This type option prevents the exception from being applied to scripts.

----------------- ----------------- ----------------- ----------------- 

													



## Options in blocking rules

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Options%20in%20blocking%20rules.png" width="750">

||ads.example.com^$script,image,domain=example.com|~foo.example.info
Rule parts

|| — Matching the beginning of an address. http://, https://, ws://, wss:// at once;

ads.example.com — Verbatim text. This text must be present in the address to be blocked;

^ — Separator. The address must either end here or a separator character like ? or / has to follow;

$ — option separator. This character indicates that the following text defines filter option;

script, image — Restriction by content type. Type options define request types to be blocked.

domain — Domain option. Limits the rule application area to a list of domains (and their subdomains).


----------------- ----------------- ----------------- ----------------- 

## Comments

For additional explanation you should use this "!" symbol at the beginning of the rule that indicates a comment (!This is a comment)

<img src="https://github.com/TheHasagi/AdguardKnowledgeBase/blob/master/pages/02.general/17.cheat-sheet/images/Comment.PNG" width="700">


----------------- ----------------- ----------------- ----------------- 

## Basic exception rules

@@||ads.example.com/notbanner^$~script

#### Rule parts

@@ — Exception marker. Rules starting like this are exceptions, they will override blocking rules. 

|| — Matching the beginning of an address. http://, https://, ws://, wss:// at once.

ads.example.com/notbanner — Verbatim text. This text must be present in the address to be blocked.

^ — Separator. The address must either end here or a separator character like ? or / has to follow.

$ — option separator. This character indicates that the following text defines filter option.

~script — Restriction by content type. This type option prevents the exception from being applied to scripts.

## Exception for an entire site

@@||example.com^$document

#### Rule parts

@@ — Exception marker. Rules starting like this are exceptions, they will override blocking rules.

|| — Matching the beginning of an address. http://, https://, ws://, wss:// at once.

ads.example.com/notbanner — Verbatim text. This text must be present in the address to be blocked.

^ — Separator. The address must either end here or a separator character like ? or / has to follow.

$ — option separator. This character indicates that the following text defines filter option.

document — Whole exception. This option completely disables blocking for corresponding pages.

----------------- ----------------- ----------------- ----------------- 

## [Cosmetic rules](https://kb.adguard.com/general/how-to-create-your-own-ad-filters#cosmetic-rules-1)

! Intro text

Introduction into CSS selectors (https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Selectors)

* [Cosmetic rules](#cosmetic-rules)
   
   Introduction into [CSS selectors](https://adblockplus.org/filter-cheatsheet#elementselection)

    Selector | Description
    ------------ | -------------
    div[class="banners"] | Matches the element with the unique class `banners`: ![image](https://user-images.githubusercontent.com/8361299/27262479-6515da62-5460-11e7-8ca8-a097e369787b.png)
    #banners | Matches all elements with ID `banners`:    ![image](https://user-images.githubusercontent.com/8361299/27262517-b9b070dc-5460-11e7-95ba-ca799745d007.png)
    div[class^="advert"] | Matches div elements that start with class `advert`: ![image](https://user-images.githubusercontent.com/8361299/27262695-e048012a-5464-11e7-8a2b-b2996426803e.png)
    div[class$="banners_ads"] | Matches div elements that end with class `banners_ads`: ![image](https://user-images.githubusercontent.com/8361299/27262734-b0f3ced0-5465-11e7-9f54-e7accd58e60f.png)
    a[href="http://example.com/"] | Matches links to http://example.com/: ![image](https://user-images.githubusercontent.com/8361299/27262625-5d369fc2-5463-11e7-8f9d-1a85e26ab91a.png)
    a[href^="http://example.com/"] | Matches links to any pages hosted on http://example.com/: ![image](https://user-images.githubusercontent.com/8361299/27262644-b8a874fc-5463-11e7-974a-82fe90d54338.png)



    * Example 1: Element hiding rule for a particular domain
`example.com##div[class="adverts"]`
    * Example 2: Element hiding exception rule
`example.com#@#div[class="adverts"]`
    * Example 3: CSS rule
       * Remove backgroung image:
`example.com#$#body { background: none!important; }`
       * Change element height for avoid primitive ad blocking detection:
`example.com#$#div[id^="ad_"] { height: 1px!important; }`



</details>

>

! End text
