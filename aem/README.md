# Links to pages on AEM and CQ related stuff

- [&Tips un Tricks](aem_tips_and_tricks.md)

## Using the list of bundles

### First Approach - html

The URL `/system/console/bundles` renders a list of all deployed bundles and gives information about them.

```
...
370	 Adobe :: SuiteTech :: Nativecommcom.adobe.suitetech.nativecomm	2.0.8	sharedcloud	Active	
512	 Adobe AEM Serialization Testercom.adobe.cq.cq-serialization-tester	1.0.10		Active	
...
```

The above renders a list as html page. Nice for browsers - bad for automation.

### Second Approach - JSON-Text
Appending `.json` (system/console/bundles.json) produces the same list but as JSON:

```
nb-syngeni350-2:clone_and_build vbe$ curl --silent  http://admin:admin@vm-uum-docker:4502/system/console/bundles.json|more
{"status":"Bundle information: 511 bundles in total, 500 bundles active, 9 bundles active fragments, 2 bundles installed.","s":[511,500,9,0,2],"data":[{"id":0,"name":"System Bundle","fragment":false,"stateRaw":32,"state":"Active","version":"4.6.1.B001","symbolicName":"org.apache.felix.framework","category":""},{"id":302,"name":"Abdera Client","fragment":false,"stateRaw":32,"state":"Active","version":"1.0.0.R783018","symbolicName":"org.apache.abdera.client","category":""},{"id":303,"name":"Abdera Core","fragment":false,"stateRaw":32,"state":"Active","version":"1.0.0.R783018","symbolicName":"org.apache.abdera.core","category":""},{"id":304,"name":"Abdera Extensions - Media","fragment":false,"stateRaw":32,"state":"Active","version":"1.0.0.R783018","symbolicName":"org.apache.abdera.extensions-media","category":""},{"id":305,"name":"Abdera Extensions - OpenSearch","fragment":false,"stateRaw":32,"state":"Active","version":"1.0.0.R783018","symbolicName":"org.apache.abdera.extensions-opens
```

### 3rd Approach - JSON-Objects
OK, we can do better: Let's pipe it through [JQ](https://stedolan.github.io/jq/):

```
nb-syngeni350-2:clone_and_build vbe$ curl --silent http://admin:admin@vm-uum-docker:4502/system/console/bundles.json|jq
{
  "status": "Bundle information: 511 bundles in total, 500 bundles active, 9 bundles active fragments, 2 bundles installed.",
  "s": [
    511,
    500,
    9,
    0,
    2
  ],
  "data": [
    {
      "id": 0,
      "name": "System Bundle",
      "fragment": false,
      "stateRaw": 32,
      "state": "Active",
      "version": "4.6.1.B001",
      "symbolicName": "org.apache.felix.framework",
      "category": ""
    },
    {
      "id": 302,
      "name": "Abdera Client",
      "fragment": false,
      "stateRaw": 32,
      "state": "Active",
      "version": "1.0.0.R783018",
      "symbolicName": "org.apache.abdera.client",
      "category": ""
    },
```

Again: better. But there's still room for improvement:

### 4th Approach - JSON-Object, filters and string interpolation

By applying filters and string interpolation we can have a list with all deployed bundles, their version and status

```
curl http://admin:admin@vm-uum-docker:4502/system/console/bundles.json | jq '.data[] | (.symbolicName + " : " + .version + " ( " + .state + " )") '

com.day.commons.osgi.wrapper.joda-time : 1.6.0.0002 ( Active )
"json : 20160810.0.0 ( Active )"
"log4j.over.slf4j : 1.7.6 ( Active )"
"com.adobe.forms.common.adobe-xfaforms-common : 4.4.32 ( Active )"
"com.day.cq.wcm.cq-wcm-mobile-qrcode : 5.8.4 ( Active )"
"org.mongodb.mongo-java-driver : 3.6.1 ( Active )"
"com.adobe.cq.myspell : 1.6.0 ( Active )"
"com.day.cq.dam.commons.nekohtml : 0.9.5 ( Active )"
"org.apache.jackrabbit.oak-blob : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-commons : 1.2.16 ( Active )"
"com.adobe.granite.repository : 1.1.94 ( Active )"
"org.apache.jackrabbit.oak-core : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-auth-external : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-auth-ldap : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-lucene : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-mk-api : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-solr-osgi : 1.2.16 ( Active )"
"org.apache.jackrabbit.oak-tarmk-standby : 1.2.16 ( Active )"
"ojdbc6-osgi : 11.2.0.3_0 ( Active )"
"org.apache.oltu.commons.json : 1.0.0 ( Active )"
"org.apache.oltu.jose.jws : 1.0.0 ( Active )"
"org.apache.oltu.oauth2.authzserver : 1.0.0 ( Active )"
"org.apache.oltu.oauth2.common : 1.0.0 ( Active )"
"org.apache.oltu.oauth2.jwt : 1.0.0 ( Active )"
"org.apache.oltu.oauth2.resourceserver : 1.0.0 ( Active )"
"com.adobe.granite.poi : 2.0.0.CQ610-B0001 ( Active )"
"com.adobe.granite.scribe : 1.3.8 ( Active )"
"com.adobe.granite.tagsoup : 1.2.1 ( Active )"
"rngom : 20120531.0.0 ( Active )"
"rideau : 77.502457.1 ( Active )"
"slf4j.api : 1.7.6 ( Active )"
"com.adobe.cq.social.cq-social-console-dns-impl : 1.0.1 ( Active )"
"com.day.commons.osgi.wrapper.svnkit : 1.3.0.0002 ( Active )"
"com.adobe.cq.com.adobe.cq.projects.wcm.core : 0.1.6 ( Active )"
```

### 5th - same as above but manager friendly

If you the colon `:` with comma `,` you can have this list an an excel compatible format:
```
curl http://admin:admin@vm-uum-docker:4502/system/console/bundles.json | jq '.data[] | (.symbolicName + "," + .version + "," + .state ) '
    
"com.adobe.osgi.wrapper.coretech.fontengine,70.459844.3,Active"
"com.adobe.livecycle.formsportal-bundle,4.4.14,Active"
"AGL_min,1.5.698416.2,Active"
"com.adobe.granite.auth.saml,0.3.32.CQ610-B0010,Active"
"com.adobe.granite.activitystreams,0.0.42,Active"
"com.adobe.granite.asset.api,2.0.4,Active"
"com.adobe.granite.asset.core,2.2.22.CQ610-B0007,Active"
"com.day.cq.cq-authhandler,5.6.26.CQ610-B0004,Active"
"com.adobe.granite.bundles.json,20090211.0.0.1,Active"
"com.adobe.granite.auth.cert,0.0.14,Active"
"com.adobe.granite.cloudsettings.core,1.0.8,Active"
"com.adobe.granite.comments,1.0.16,Active"
"com.adobe.granite.confmgr,1.0.0,Active"
"com.adobe.granite.contexthub.commons,0.0.36,Active"
"com.adobe.granite.crx-explorer,1.0.30,Active"
"com.adobe.granite.crx-packagemgr,1.0.62.CQ610-B0010,Active"
"com.adobe.granite.crxde-lite,1.0.88.CQ610-B0010,Active"
"com.adobe.granite.crypto,3.0.18.CQ610-B0004,Active"
"com.adobe.granite.csrf,1.0.8.CQ610-B0004,Active"
"com.adobe.granite.frags.impl,0.0.2,Active"
```
