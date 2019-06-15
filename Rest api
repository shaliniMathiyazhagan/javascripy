const http=require("http")
const mysql=require('mysql');
const express=require('express');
var app=express();
const bodyparser= require('body-parser');
app.use(bodyparser.json());
app.use(express.json());
app.use(bodyparser.urlencoded({ extended: true }));
var path=require('path');
const router=express.Router();
router.get('/employee',function(req,res)
{
res.sendfile(path.join(Nodejs+'post.html'));
});
var mysqlconnection = mysql.createConnection({
host:'northside.in',
user:'shakir',
password:'sh akir123',
database:'shakir_test'
});
mysqlconnection.connect((err)=>{
if(!err)
console.log('succesfully db connected');
else
console.log('failed connection \n error:'+JSON.stringify(err,undefined,2));
});

app.listen(3000,()=>console.log('express server is runnig at port no:3000'))
//get all employees
app.get('/employee',(req,res)=>{
mysqlconnection.query('select * from project_shalu',(err,rows,fields)=>{
if(!err)
res.send(rows);
else
console.log(err);
})
});
//particular employee id
app.get('/employee/:id',(req,res)=>{
var id=req.query.id;
mysqlconnection.query('select * from project_shalu where id=?',[req.query.id],(err,rows,fields)=>{
if(!err)
res.send(rows);
else
console.log(err);
})
});
//delete an employee particular id
app.delete('/employee/:id',(req,res )=>{
mysqlconnection.query('Delete from project_shalu where id=?',[req.params.id],(err,rows,fields)=>{
if(!err)
res.send('deleted succesfully.');
else
console.log(err);
})
});
//post method--
app.post('/employee',function(req,res){
var postData=[req.body.id,req.body.name,req.body.Department];
mysqlconnection.query("Insert into project_shalu SET id=?,`name`=?,`Department`=?",postData,function (error,results)
{
if (!error)
res.end('inserted');
});
});
//put method---
app.put('/employee',function (req,res){
mysqlconnection.query('update project_shalu SET Department=? where id=?',
[req.body.Department,req.body.id],function (error,results,fields){
if(err)throw err;
res.end(JSON.stringify(results));
});
});

