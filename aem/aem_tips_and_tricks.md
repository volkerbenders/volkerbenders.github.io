# AEM Tips & Tricks

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [AEM Tips & Tricks](#aem-tips-tricks)
	- [I started using Adobe AEM in January 2016.](#i-started-using-adobe-aem-in-january-2016)
	- [Where AEMs data lives](#where-aems-data-lives)
	- [One of my first learnings was that AEM uses a filebased datastore - called tarmk.](#one-of-my-first-learnings-was-that-aem-uses-a-filebased-datastore-called-tarmk)
	- [Move an AEM in filesystem](#move-an-aem-in-filesystem)
	- [Status of all Bundles](#status-of-all-bundles)

<!-- /TOC -->

# Repository Maintenance
AEMs TarMK can grow really huge. There're ways to deal with it - trimming its size by either
* remove everything you don't need anymore or
* create a new repo with only content you need right now

The first approach is also known as garbage collection or offline tar compaction.
The latter one is often more efficient and yields a smaller result size.

```bash
$> java -jar ~/crx2oak-1.6.8-all-in-one.jar --src-datastore=/opt/aem/datastore --datastore=$HOME/datastore-new --exclude=/var/audit --copy-versions=false segment-old:repository segment-old:$HOME/repository-new
```

# Activate entire JCR Trees

AEMs publisher has a function called "Activate Tree":
http://<PUBLISHER IP OR NAME>:4501/etc/replication/treeactivation.html


# Templates

When setting up a new site i relied on

- [Templates Basics](https://docs.adobe.com/docs/en/aem/6-1/develop/the-basics/templates.html#Templates)
  -> The part about ~Template Availability~ was very useful.
  Very usefull is the diagram on the ~template evaluation~ process.

pretty much

# AEM & CLI
- [Some cURL commands](http://www.aemcq5tutorials.com/tutorials/adobe-cq5-aem-curl-commands/)

## I started using Adobe AEM in January 2016.
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

## Configuration

### Configure Log-Files

You can manage log files using [Web Console](http://vm-uum-docker:4502/system/console/slinglog)
Loggers can be added, deleted and modified there

# JCR Queries

List of Pages providing examples on how to query the JCR:
- [http://labs.6dglobal.com/blog/2014-10-07/9-jcr-sql-2-queries-every-aem-dev-should-know/](http://labs.6dglobal.com/blog/2014-10-07/9-jcr-sql-2-queries-every-aem-dev-should-know/)
- [Queries by my coworker florian](https://gist.github.com/floriankraft/8b3720464318cd5cd9e2)
- [https://apiltamang.wordpress.com/2016/10/21/list-of-jcr_sql2-queries-ive-had-to-use-as-an-aem-developer/](https://apiltamang.wordpress.com/2016/10/21/list-of-jcr_sql2-queries-ive-had-to-use-as-an-aem-developer/)
