# Http
基于libuv封装的http server client
服务端用法

void server(Request& req,Response& res)
{
	cout<<req.url<<endl;
	res.writeOrEnd("hello",true);

}
Server server(server);
server.listen("0.0.0.0",9009);

客户端用法
GET
void resFunc(Response& res)
{
	cout<<res.body<<endl;
	

}
void error(const string& err)
{
	if (err.size()>0)
	{
		cout<<err.c_str()<<endl;
	
	}
}

Client client;
client.setTimeOut(3000);
client.get("https://www.baidu.com/",resFunc,error);

POST  OR GET
Client client;
Options opt;
opt.method="POST";
opt.host="localhost";
opt.port = 8080;
opt.url = "http://localhost:8080/edu/test/test2.json/";
opt.content="username=hello&password=world";
opt.content_length = opt.content.size();
opt.content_type="application/x-www-form-urlencoded";
client.request(opt,resFunc,error);


