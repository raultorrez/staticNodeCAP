# staticNodeCAP
**PASOS A SEGUIR:**  
**PASO-1:**  
: descargar e instalar node js  
**PASO-2:**  
: verificar la instalacion de node.js y npm con los comandos **node -v** y **npm -v** 
**PASO-3:**  
: crear una carpeta para su proyecto con el comando **mkdir** y luego ingresara a la carpeta
**PASO-4:**  
:crear el package.json con el comando **npm init** rellenar lo pedido la instalacion, instalar node statico **npm install node-simple-static-server** 
**PASO-5**      
: instalar http con el comando **npm install http**  
**PASO-6**  
:instalar livereload con el comando **npm install livereload** 
**PASO-7**  
: crear una carpeta en la raiz llamada **public**  
**PASO-8**  
:dentro de la carpeta crear una archivo **index.html** 
**PASO-9**  
: copiar el Script dentro del achivo **index.html** :
 ~~~
<script>
        
document.write('<script src="http://' + (location.host || 'localhost').split(':')[0] +
          
':35729/livereload.js?snipver=1"></' + 'script>')
    
</script>
~~~
 
**PASO-10**  
:crear un archivo **server.js** en la raiz de la carpeta y copiar este codigo:
~~~
var nodestatic = require('node-static'),
    
port = 5454 ///tener en cueta el puerto en el q trabajara el servidor
    
http = require ('http');

var file = new nodestatic.Server('./public',{//public es la carpeta en la que estan nuestros archivos
    
cache:3600,
    
gzip:true
    

});


http.createServer(function(request, response){
    
request.addListener('end', function(){
        
file.serve(request,response);
        
    
}).resume();
}).listen(port);


var livereload=require('livereload');

var server=livereload.createServer({
    
exts:['html','css','js']
});
server.watch(__dirname+"/public");
console.log("sevidor cargando puerto "+port);
~~~
**PASO-11**
:levatar el servidor en la consola con los comandos **node server.js**

**PASO-12**
ingresar al navegador y escribir **localhost:5454** //5454 es el numero del puerto que se esta usando

**PASO-13**
:descargar y ejecutar **ngrok**

**PASO-14**
:escribir en la consola q saldra **ngrok.exe http 5454**
