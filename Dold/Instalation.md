Instalation:
---
__nodejs installieren
express installieren__

express, in commandline ausführen und view-engine angeben mit: 
express --view=ejs

wir entschieden uns für ejs, da es normale html-tags verwendet.

bei den js embedded tags gilt es zu unterscheiden zwischen:

__<% %>, in welchen code läuft;
<%= %>, in welchen text ausgegeben wird;
<%- %>, mit welchen man andere ejs snipplets includen kann.__



im app.js werden die routes und benötigte middleware gesetzt.
in diesem fall haben wir die routes ausgelagert in das File router.js

```
var web = require('./web/controller/router'); //<-- router von unten
var app = express();
app.use('/', web);
```



Routes werden dann durch ein express-router-objekt definiert.

```
const express = require('express');
const router = express.Router();
```



Beim router kann man routes mit methoden festlegen, der name entspricht dabei der anzunehmenden HTTP-Methode.

```
router.get("/todo/:id", index.one);
router.post("/create", index.create);
router.put("/todo/:id", index.update);
router.delete("/todo/:id", index.delete);
```



Es gibt req, welches alle information der request enthält. In ihm sind alle möglichen daten vom client an den serv enthalten und auch die session.

Es gibt res, welches die ausgabe enthält. Verschiedene möglichkeiten... (json, send, render)



render macht res.render(__<<seite, die angezeigt werden soll>>__, __<<parameter, mit denen das ejs handeln soll>>__);





__include in ejs:

```

<!DOCTYPE html>

<html>

 <body>

  <%- include('templates/navbar',{title}) %>

    <div class="container mt-5">

   <h1><%= title %></h1>

  </div>

  

 </body>

</html>

```
resultat
---

Startseite mit übersicht:

![image-20200311164614158](C:\Users\morpl\AppData\Roaming\Typora\typora-user-images\image-20200311164614158.png)

Hochladen:

![image-20200311164643935](C:\Users\morpl\AppData\Roaming\Typora\typora-user-images\image-20200311164643935.png)

Bearbeiten und löschen:

![image-20200311164803549](C:\Users\morpl\AppData\Roaming\Typora\typora-user-images\image-20200311164803549.png)