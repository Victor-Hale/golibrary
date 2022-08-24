# golibrary
本仓库是golang  有用的一些库
2022/8/24  
## 第一次添加包 log  database  jwt
适用于web开发中的日志处理，持久化数据库，jwt方法等
### log
Info = log.New(io.MultiWriter(file, os.Stderr), "INFO: ", log.Ldate|log.Ltime|log.Lshortfile)
Error = log.New(io.MultiWriter(file, os.Stderr), "ERROR: ", log.Ldate|log.Ltime|log.Lshortfile)
use this
log.Error.Println("连接失败；",err)
### database
open()  //打开数据库，初始化数据
Close() //关闭数据库
Get()//从表table的记录里读取主键为key的记录的值
{
传入map  db *Database  ......data map[string]map[string][]byte  
入参  table, key string
}
set()向表table添加一条记录，主键为key, 值为val
{
传入map  db *Database  ......data map[string]map[string][]byte  
入参  table, key string, val []byte
}
NewDatabase  //创建一个Database对象
IsNotExists   //判断文件是否不存在，如果不存在返回true 
### jwt
RefreshToken(tokenString string)//刷新jwt token
{
入参  tokenString string
}
//验证jtw token
ValidateToken(tokenString string) (info User, err error){}
//获取jwt token
func GenerateToken(info *User, expiredSeconds int) (tokenString string, err error){}
// return this result to client then all later request should have header "Authorization: Bearer <token> "
GetHeaderTokenValue(tokenString string) string {}
//生成has256加盐加密
func HashAndSalt(pwdStr string) (pwdHash string, err error) {}
// 验证密码
func ComparePasswords(hashedPwd string, plainPwd string) bool {}
..........等等
  
  
