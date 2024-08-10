// // console.log("hello from server");
// // console.log("hello again");

// //set timeout is a pre defined function in js

// console.log("1")
// setTimeout(()=>{
//     console.log("2")
// },1000)
// console.log("3")

// setInterval(()=>{
//         console.log(" trisha samanta")
//     },1000)


// const http=require('http')
// http.createServer(function(req,res){
//     res.writeHead(200,{'Content-Type':'text/plain'});
//     res.end("ashik")
// }).listen(8080)



const http=require('http');
const dotEnv=require('dotenv');
dotEnv.config();
//const PORT=process.env.PORT
const express=require('express');
let app=express();
const router=require('./routes/api-route.js');

require('./config/database')();

// let server=http.createServer(function(req,res){
//     res.writeHead(200,{'Content-Type':'text/plain'});
//     res.end("hello world")
// })

//app.use(express.static('public'))
//app.use(express.static(path.join(__dirname,"public")))
app.use('/api',router.route);

app.get('/user/list',function(req,res){
    res.send({
        // "message":"hello",
        data:[
                    {firstName:"Papai", 
                        lastName:"Ghosh"},

                    {firstName:"Puja", 
                        lastName:"Roy"},

                    {firstName:"Suvendu",
                        lastName:"Bag"}
                ],
        status:"sucess"
        
    })
}
)
const server=http.createServer(app);
server.listen(process.env.PORT,function(err){
    if(err)throw err;
    console.log(`Server is runung on port:${process.env.PORT}`)
})
// server.listen(PORT,console.log(SERVER running on ${PORT}))
