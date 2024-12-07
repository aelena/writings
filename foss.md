
⚠️ __About__: this was written a long time ago as a sort of guidelines document gathering the different aspects to take into account when evaluating potential use of FOSS in the design and implementation of new systems.

___

# Notes on Adopting FOSS

FOSS, or FLOSS, meaning Free/Libre/Open Source Software is undeniable a very viable alternative in the software development process, when compared with Proprietary Software or Closed Source Software. But since the quality of FOSS projects or products can and does vary widely, there has to be some careful evaluation of this type of software assets.

Next gen companies are constantly redefining development practices very often leveraging open source software, if not contributing directly to existing projects or creating new projects that sometimes become new industry standards. It is an undeniable force of innovation.

Even MS has turned to Open Source since the advent of Satya Nadella, so Open Source is already the new medium for companies and developers working with MS technology too, which was not so much the case a decade ago.


## The basic criteria

When looking at open source alterntives or considering using open source software as part of your larger system (databases, libraries or frameworks), or even as a tool or secondary role in your system (for example, helper tools) it is necessary to consider certain aspects. These are basic questions that are relevant to the selection process.

It is tempting to download and run, but some things need to be considered (in no particular order here):

- **The different FOSS licenses and their legal implications**; not all licenses are equal. MIT license is preferred.
- **Solution assessment and feasibility**, as with any other solution/technology 
  - what value is it bringing to the table?
  - what are the options for safe integration? 
  - does it bring other dependencies to the picture that you need to be aware of?
- **Code quality**. Examine the code, clone the repo and run it through your SAST of choice maybe. Check the stars or ratings in GitHub, for sure.
  - What is the overall quality of documentation, readmes etc? 
  - overall feel of the documentation, details, if there are also issues, questions and valid answers to those
- **Life Expectancy**
  - is this project being actively maintained? 
  - How long has the project been in existence?
  - Can we see that developers actually respond to filed bugs?
  - who are the sponsors of the project, if any?
  - does it look like there is a roadmap behind? 
  - Is there a vibrant community (books, events, etc)?
  - Is it maintained by a reputed vendor or does it have a community around it in GitHub, how many stars? 
- **Consider the security implications**, there have been packages and libraries with malware in it, for example, for mining crypto
  - Does the site for the project show for example that developers & maintainers have taken care of security issues that might have been reported in the past? 
  - Be aware that [supply chain attacks](https://en.wikipedia.org/wiki/Supply_chain_attack) are becoming a frequent vector
  - Research public vulnerabilities for the project, package or framework  
- **Risk management** and not only for security, also from the point of view of what is the impact to my solution if the FOSS piece disappears, or if it changes its license, stops being maintained, its vendor closes shop or is acquired and terms change?
  - Basically, consider the implications for your software supply chain. Your project using FOSS might in turn be a dependency for a third system, so a disruption in a FOSS component can bubble downstream with unforeseen side effects. 
- **Life Span of your solution** that incorporates FOSS
- **Lifecycle, Patching, Decommissioning / Migration** to better alternatives that might appear later
- **Complexity Management** – OSS is often opinionated and your teams might have to deal with different styles, frameworks and approaches.
- **Managing Coherence** in tech stack and ecosystem, as well as infrastructure
- **Incremental change or Evolution** - what happens when a FOSS dependency changes between version 1.0 and version 1.1? It is important to identify the source code that changed, especially for vital FOSS components with major version changes. This is relevant because 
  - new dependencies or components may have been introduced, or also bugs and vulnerabilties
  - or might have been retired, 
  - or again, the license on a software component may have changed between versions
- **Hidden costs** - consider the hidden costs in apparently "free" software, such as hardware, failures or downtime, engineer time needed to run or support and cognitive load.
<br/>

## Strategy

- Identify which OSS components your current applications might already be using (it's important to know the potential security risks). At least 80% of developers are already doing it, explicitly or not. At a higher maturity level, OSS use must be continuously monitored (this can be part of CI/CD pipelines)
- As with COTS, FOSS also requires you to do your due diligence on quality, security, scalability etc
- Search for known vulnerabilities in FOSS in existing databases. Be aware that vulnerabilities in FOSS are public knowledge. 
  - [Open Source Vulnerabilities](https://osv.dev/list), which covers Python (PyPI) packages and npm among others. This is a Google project, read more about it [here](https://security.googleblog.com/2021/02/launching-osv-better-vulnerability.html)
  - Search the US [National Vulnerability Database](https://nvd.nist.gov/products/cpe/search)
  - There are others, but they are commercial offerings and we leave them out of the scope of these recommendations
  - Define OSS Policy (acceptable licenses, percentages etc) and automate compliance that are adequate with your project
- Customers have to be warned out OSS in products (there can be legal ramifications due to different outlooks on the use of FOSS)
- Visibility into OSS evolution and potential issues, which can be different from "classic" vendor software. Might require more DIY than COTS or ability and willingness to fork products
- Open Source Competence is like any other, and needs to be grown. Deliver a roadmap. Ensure commitment from Management.
- Leverage the ecosystem of OSS Vendors
- Open code is not open source. Watch for “enterprise” editions or products with no community behind
<br/>

## Common misconceptions

Common misconceptions about OSS still endure, but it is possible to counter all the claims immediately:

- **Low quality** - *but strong (not all, of course) open source projects adopt strict quality processes, which an organization can also adopt for its own benefit. And it is not like closed source software goes without flaws, breaches and (in)famous examples of low quality products. Neither is guaranteed to avoid breaches.*
- **Open source software is free** - *not necessarily, and some might have paid support models, or a variation of freemium* 
- **Open source software is for Linux** - *as well as for Windows in a huge majority of cases*
- **Lack of support**, *although being a risk to consider with smaller or individual projects, is not a reality anymore as there is a thriving OSS ecosystem with many very stable projects. Of course, not all FOSS projects are created equal, so again some degree of due dilligence is needed.*
- **Using open source software requires you to open your code** - *well, that very much depends on the license, which is why you need to be aware of what the license requires before you use open source software.* Some licenses have rules for contributing back changes you make. Contributing back is often beneficial but might not be an option in specific cases where there is strategic IP involved.
- **Open Source is safer and more secure**, as in the famous adage, “given enough eyeballs all bugs are shallow” - *except that using OSS is not excusing you from due diligence, monitoring and problems – think the Heartbleed OpenSSL issue*
- **No one gets paid to write open source** - *except all of those working in the thriving OSS ecosystem*
<br/>
## Top 10 risks associated with the use of FOSS

Be aware of the main risks that you face with the use of FOSS.

1.  __Security vulnerabilities__: One of the main risks associated with the use of open source software is the potential for security vulnerabilities. Since the source code is publicly available, it is more vulnerable to being exploited by hackers or other malicious actors. To remediate that, only use open source software from reputable sources, since many vendors today have lots of freely available libraries, so where possible always stick to official SDKs, libraries etc.
    
2.  __License compliance__: Another risk associated with open source software is the potential for license compliance issues. Some open source licenses have strict requirements for how the software can be used and distributed, and failure to comply with these requirements can result in legal and financial consequences.
    
3.  __Quality__: While open source software can be of high quality, there is also the risk that it may not be as reliable or robust as proprietary software. This can be especially problematic in mission-critical applications where a failure could have significant consequences. Consider what type of application you are building from all angles, operational, SLAs, confidentiality and so on and carefully consider if a paid for tried and tested commercial alternative would not be a better fit and save you problems down the line as opposed to the use of some FOSS that might introduce risks now or later, both in security and/or maintenance (support).
    
4.  __Support__: Open source software is often developed and maintained by a community of volunteers, and as a result, there may be limited options for technical support. This can make it more difficult to resolve issues or get assistance when problems arise. So, consider that in relation to what was said in the previous point about business critical applications or services.
    
5.  __Compatibility__: Compatibility issues can also be a risk when using open source software, especially if it is not well-documented or tested against other software or hardware.
    
6.  __Integration__: Integrating open source software with other systems or applications can be challenging, and there may not be clear documentation or support available to help with the process.
    
7.  __Upgrades and maintenance__: Upgrading and maintaining open source software can also be more complex and time-consuming than proprietary software, as there may not be a single organization responsible for maintaining and updating the codebase.
    
8.  __Customization__: Customizing open source software may also be more difficult than proprietary software, as there may not be as many resources available to help with the process. On the other hand, you are free to fork the project but that adds new work and responsibilities that tend to remain permanent, which can become a drain on current capacity. 
    
9.  __Documentation__: Documentation for open source software can also be limited or outdated, which can make it more challenging to use and understand. Work with well-documented projects that provide good documentation, fully featured code examples and where you can see there is active communication going on.
    
10.  __Community involvement__: Finally, the level of community involvement in an open source project can vary significantly, and this can impact the quality, reliability, and support of the software. If the community around a particular open source project is not active or engaged, it may be more difficult to get help or resolve issues.

<br/>

## A (very) short overview of licenses
OSS Licenses is not a simple topic, this is the most cursory introduction to the topic. There are many licenses and the devil is in the details, but at a high level, we can group them broadly into
- Low risk or permissive (Apache, MIT are the most popular/frequent). These are preferred.
- Medium risk, or semi-permissive (Mozilla, Eclipse and others)
- High risk, or restrictive (GPL 3.0, AGPL)

Risk is considered here from a proprietary IP point of view, therefore, licenses such as GPL 3.0 might, in a worst case scenario, require the release of proprietary software under the same license—royalty-free. Most open source projects, even those with rules for contributing back code, are distributed as libraries that you can link into your own code without opening the functions you write yourself (for instance, the GNU Lesser General Public License).

The MIT License is preferred as it gives the most freedom being the simplest of those licenses, imposing almost no restrictions on licensees and no meaningful restriction at all on licensees distributing derivative works.

*Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software*

Going into comparing all available licenses could fill an entire book, so we will not cover these in details. Due Dilligence in each case should be done by project technical leads. We can also support the decision process.

A high level comparison of licenses can be seen in Wikipedia
https://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licences

Further reference into this topic
https://www.synopsys.com/blogs/software-security/top-open-source-licenses/
https://en.wikipedia.org/wiki/Comparison_of_free_and_open-source_software_licenses
