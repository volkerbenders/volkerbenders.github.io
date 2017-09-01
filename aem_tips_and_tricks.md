# AEM Tips & Tricks

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [AEM Tips & Tricks](#aem-tips-tricks)
	- [I started using Adobe AEM in January 2016.](#i-started-using-adobe-aem-in-january-2016)
	- [Where AEMs data lives](#where-aems-data-lives)
	- [One of my first learnings was that AEM uses a filebased datastore - called tarmk.](#one-of-my-first-learnings-was-that-aem-uses-a-filebased-datastore-called-tarmk)
	- [Move an AEM in filesystem](#move-an-aem-in-filesystem)
	- [Status of all Bundles](#status-of-all-bundles)

<!-- /TOC -->

## I started using Adobe AEM in January 2016.
Since it is a quite complex technology stack i had to question the internet a lot to answer my questions.
This is a Collection of my findings and maybe they're useful to somebody.

## Where AEMs data lives
```bash
nb-syngeni350:author-cq61 vbe$ tree -L 2 -d
.
└── crx-quickstart
    ├── app
    ├── bin
    ├── conf
    ├── install
    ├── launchpad
    ├── logs
    ├── monitoring
    ├── opt
    └── repository    <-- Data lives here
```
## One of my first learnings was that AEM uses a filebased datastore - called tarmk.
As per default everything you store in AEM stays there forever. Eventually stuff gets flagged as deleted - but still consumes space on your disk.

## Move an AEM in filesystem
We had the need to move an installed AEM on the filesystem. I moved the entire AEM installation folder from one folder to another. I considered me done. I was not.
AEM still started but the servers error.log contained a lot of (a that time) strange error messages.
The reason was it couldn't find the datastore aka repository.

The FileDataStore location can be changed in a file called
```
install/org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg
```

with the content

```bash
path=$AEM_SERVERS/author-cq61/crx-quickstart/repository/repository/datastore
minRecordLength=4096
```
It should work with relative paths, too. But i haven't tested it yet.

## Status of all Bundles
```bash
curl --silent http://admin:admin@127.0.0.1:4502/system/console/bundles.json \
        |jq '.data[] | .state + ": " + .name + " (" + .version + ")"' -
```

## Useful AEM-Links

- [Dump ClientLibs](http://localhost:4502/libs/granite/ui/content/dumplibs.html)
  To View all configured clientlibs (js, css,...) and their respective contents you can use the *dumplibs* page
### Touch-UI
- [Sites](http://127.0.0.1:4502/sites.html)

### Classic UI
- [SiteAdmin - ClassicUI](127.0.0.1:4502/siteadmin#/content)
### Dump Clientlibs



## HTL Template Language

- [Getting started](https://docs.adobe.com/docs/en/htl/docs/getting-started.html)
- [Introducton by Feike Visser](http://blogs.adobe.com/experiencedelivers/experience-management/htl-intro-part-1/)
- [Java Use API](https://docs.adobe.com/docs/en/htl/docs/use-api/java.html)
- [Custom Async Clientlibs](http://www.nateyolles.com/blog/2016/06/custom-aem-html5-async-clientlibs)
- [Sightly Quick Reference](http://aemtuts.com/aem-sightly-quick-reference/)
- [Calling Clientlibs from HTL](http://blogs.adobe.com/experiencedelivers/experience-management/htl-clientlibs/)
- [Using Client-Side Libraries](https://docs.adobe.com/docs/en/aem/6-2/develop/the-basics/clientlibs.html)
