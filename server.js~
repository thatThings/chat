//客户端HTTP模块
var http = require("http");//引入模块
var fs = require("fs");//引入文件系统模块
var ws = require("socket.io");
var server = http.createServer(function(req,res){
    //对当前连接web服务器进行处理
    console.log("ok");
    //读取文件流
    var html = fs.readFileSync("./client.html");
    res.end(html);//向连接的客户端发送信息
});//搭建web服务实例
//npm i socket.io
server.listen("3003");//监听端口
var io = ws(server);//生成socket服务端，用户可以直接用过访问web端的地址直接连接到socket
io.on("connection",function(client){
    //每一个连接的客户端，接下来要做什么时事情
    console.log("有新用户连接到聊天室")
    client.on("message",function(mes){
        console.log(mes);
        io.emit("message",mes);//io服务端主动发消息给所有的已连接的客户端
    });//监听到客户端实例所发送过来的消息
});//在socket服务中监听连接事件
