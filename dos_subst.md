# DOS - Commands
## subst

Using `subst` you can map long directory paths to simple drive letters:
```
subst <drive> <path>

e.g.
subst x: C:\Dev\source2\commons\acme-commons-apps\src\main\jcr_root
```

Means maps the path `C:\Dev\source2\commons\acme-commons-apps\src\main\jcr_root` on drive x:.
So issueing
```
C:\Users\TonyStark>dir x:
 Datenträger in Laufwerk X: ist System
 Volumeseriennummer: F6B5-5EC0

 Verzeichnis von X:\

27.01.2017  14:56    <DIR>          .
27.01.2017  14:56    <DIR>          ..
27.01.2017  14:56               511 .content.xml
27.01.2017  14:56    <DIR>          apps
12.07.2017  16:28    <DIR>          content
27.01.2017  14:56    <DIR>          acmeimport
27.01.2017  14:56    <DIR>          etc
27.04.2017  09:52    <DIR>          _oak_index
               1 Datei(en),            511 Bytes
               7 Verzeichnis(se), 53.706.199.040 Bytes frei
```

Is the same as issueing
```
C:\Users\TonyStark>dir C:\Dev\source2\commons\acme-commons-apps\src\main\jcr_root
 Datenträger in Laufwerk C: ist System
 Volumeseriennummer: F6B5-5EC0

 Verzeichnis von C:\Dev\source2\commons\acme-commons-apps\src\main\jcr_root

27.01.2017  14:56    <DIR>          .
27.01.2017  14:56    <DIR>          ..
27.01.2017  14:56               511 .content.xml
27.01.2017  14:56    <DIR>          apps
12.07.2017  16:28    <DIR>          content
27.01.2017  14:56    <DIR>          acmeimport
27.01.2017  14:56    <DIR>          etc
27.04.2017  09:52    <DIR>          _oak_index
               1 Datei(en),            511 Bytes
               7 Verzeichnis(se), 53.706.190.848 Bytes frei
```

Pretty easy, hu?!

---
