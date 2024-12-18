# GOPROG
CODES
week 1 lcm & gcd

package main

import "fmt"

func lcm(temp1 int, temp2 int) {
	var lcmnum int = 1
	if temp1 > temp2 {
		lcmnum = temp1
	} else {
		lcmnum = temp2
	}

for {
		if lcmnum%temp1 == 0 && lcmnum%temp2 == 0 {
			fmt.Printf("LCM of %d and %d is %d", temp1, temp2, lcmnum)
			break
		}
		lcmnum++
	}
	return
}
func gcd(temp1 int, temp2 int) {
	var gcdnum int
	for i := 1; i <= temp1 && i <= temp2; i++ {
		if temp1%i == 0 && temp2%i == 0 {
			gcdnum = i
		}
	}
	fmt.Printf("GCD of %d and %d is %d", temp1, temp2, gcdnum)
	return
}

func main() {
	var n1, n2, action int
	fmt.Println("Enter two psitive integers:")
	fmt.Scanln(&n1)
	fmt.Scanln(&n2)
	fmt.Println("Enter 1 for LCM and 2 for GCD")
	fmt.Scanln(&action)
	switch action {
	case 1:
		lcm(n1, n2)
	case 2:
		gcd(n1, n2)
	}
}

week 2 print pyramid of numbers

package main
import "fmt"
func main(){
              var n int
              fmt.Print("Enter the number of levels:")
              fmt.Scan(&n)
              for i:=1;i<=n;i++{
                  //print leading spaces
                  for j:=1;j<=n-i;j++{
                       fmt.Print(" ")
                  }
              //print numbers in increasing order
              for j:=1;j<=i;j++{
                  fmt.Print(j)
              }
               //print numbers in decreasing order
              for j:=i-1;j>=1;j--{
                  fmt.Print(j)
              }
           //move to next line
                fmt.Println()
            }
}


week 4 cal standard deviation in math pkg

package main

import (
	"fmt"
	"math"
)
func main() {
	var num [10]float64
	var sum, mean, sd float64
	fmt.Println("**********enter 10 elements************")
	for i := 1; i <= 10; i++ {
		fmt.Printf("enter %d element:", i)
		fmt.Scan(&num[i-1])
		sum += num[i-1]
	}
	mean = sum / 10
	for j := 0; j < 10; j++ {
		sd += math.Pow(num[j]-mean, 2)
	}
	sd = math.Sqrt(sd / 10)
	fmt.Println("the sd is:", sd)
}

week 5 print Floyd's Triangle

package main
import "fmt"
func main(){
              var rows int
              var temp int=1
              fmt.Print("Enter the number of rows:")
              fmt.Scan(&rows)
              for i:=1;i<=rows;i++{
                  for k:=1;k<=i;k++{
                       fmt.Print(" ",temp)
              temp++
                  }
fmt.Println(" ")
}
} 

week 6 take user input and addition of two strings

package main
import "fmt"
func main(){
  fmt.Print("enter first string :")
  var first string
  fmt.Scanln(&first)
  fmt.Print("enter second string :")
  var second string
  fmt.Scanln(&second)
  fmt.Print(first+second)
}

week 7 string palindrome

package main
import "fmt"
func main(){
var number, remainder, temp int
var reverse int=0
fmt.Print("Enter any positive integer:")
fmt.Scan(&number)
temp=number
for{
remainder=number%10
reverse=reverse*10 + remainder
number=number/10
if(number==0){
break
}
}
if(temp==reverse){
fmt.Printf("%d is a palindrome",temp)
}
else
{
fmt.Printf("%d is not a palindrome",)
}
}
package main
import(
"fmt"
"strings"
)
func main(){
var originalString string = "madam"
var reverseString string = ""
var length=len(originalString)

for i:=length-1;i>=0;i-- {
reverseString=reverseString + string(originalString[i])
}
if strings.ToLower(originalString)==strings.ToLower(reverseString){
fmt.Println("The given string is palindrome");
}else{
fmt.Println("The given string is not a palindrome");
}
}


week 9 calculate average using arrays

package main
import "fmt"
func main(){
var num[100] int
var temp, sum, avg int
fmt.Print("enter no of elements:")
fmt.Scanln(&temp)
for i:=0;i<temp;i++ {
fmt.Print("enter the numbers:")
fmt.Scanln(&num[i])
sum+=num[i]
}
avg=sum/temp
fmt.Printf("avg of %d numbers (s) is %d" , temp, avg)
}


week-14

package main 
import ( 
"fmt" 
"runtime" 
"sync" 
) 
 func main() { 
// Allocate three logical processors for the scheduler to use. 
runtime.GOMAXPROCS(3) 
 
// processTest is used to wait for the program to finish. var processTest sync.WaitGroup 
// Add a count of three, one for each goroutine. 
processTest.Add(3) 
 
// Declaration of three anonymous function and create a goroutine. 
go func() { defer processTest.Done() for i := 0; i < 30; i++ { for j := 51; j <= 100; j++ { fmt.Printf(" %d", j) if j == 100{ fmt.Println() 
} 
} 
} }() go func() { defer processTest.Done() for j := 0; j < 10; j++ { for char := 'A'; char < 'A'+26; char++ { fmt.Printf("%c ", char) if char == 'Z' { fmt.Println() 
} 
 
} 
} 
}() 
 
 
 go func() { defer processTest.Done() for i := 0; i < 30; i++ { for j := 0; j <= 50; j++ { fmt.Printf(" %d", j) if j == 50 { fmt.Println() 
} 
} 
} 
}() 
// Wait for the goroutines to finish. processTest.Wait() 
} 



week-13

DROP TABLE IF EXISTS `employee`; 
CREATE TABLE `employee` ( 
`id` int(6) unsigned NOT NULL AUTO_INCREMENT, 
`name` varchar(30) NOT NULL, 
`city` varchar(30) NOT NULL, PRIMARY KEY (`id`) 
) ENGINE=InnoDB AUTO_INCREMENT=1 DEFAULT CHARSET=latin1;  
 
 package main 
import ( 
"database/sql" 
"log" 
"net/http" 
"text/template" 
 
_ "github.com/go-sql-driver/mysql" ) 
 type Employee struct { 
Id int 
Name string 
City string 
} 
 func dbConn() (db *sql.DB) { dbDriver := "mysql" dbUser := "root" dbPass := "root" dbName := "goblog" 
db, err := sql.Open(dbDriver, dbUser+":"+dbPass+"@/"+dbName) if err != nil { panic(err.Error()) 
} return db 
} 
 var tmpl = template.Must(template.ParseGlob("form/*")) func Index(w http.ResponseWriter, r *http.Request) { 
db := dbConn() selDB, err := db.Query("SELECT * FROM Employee ORDER BY id DESC") if err != nil { panic(err.Error()) 
} emp := Employee{} res := []Employee{} for selDB.Next() { var id int var name, city string 
err = selDB.Scan(&id, &name, &city) if err != nil { panic(err.Error()) 
} emp.Id = id emp.Name = name emp.City = city res = append(res, emp) 
} 
tmpl.ExecuteTemplate(w, "Index", res) defer db.Close() 
} 
func Show(w http.ResponseWriter, r *http.Request) { db := dbConn() 
nId := r.URL.Query().Get("id") selDB, err := db.Query("SELECT * FROM Employee WHERE id=?", nId) if err != nil { panic(err.Error()) 
} emp := Employee{} for selDB.Next() { var id int var name, city string 
err = selDB.Scan(&id, &name, &city) if err != nil { panic(err.Error()) 
} emp.Id = id emp.Name = name emp.City = city 
} 
tmpl.ExecuteTemplate(w, "Show", emp) defer db.Close() 
} 
 func New(w http.ResponseWriter, r *http.Request) { tmpl.ExecuteTemplate(w, "New", nil) } 
 func Edit(w http.ResponseWriter, r *http.Request) { db := dbConn() 
nId := r.URL.Query().Get("id") selDB, err := db.Query("SELECT * FROM Employee WHERE id=?", nId) if err != nil { panic(err.Error()) 
} emp := Employee{} for selDB.Next() { var id int var name, city string 
err = selDB.Scan(&id, &name, &city) if err != nil { panic(err.Error()) 
} emp.Id = id emp.Name = name emp.City = city 
} 
tmpl.ExecuteTemplate(w, "Edit", emp) defer db.Close() 
} 
func Insert(w http.ResponseWriter, r *http.Request) { db := dbConn() if r.Method == "POST" { name := r.FormValue("name") city := r.FormValue("city") 
insForm, err := db.Prepare("INSERT INTO Employee(name, city) 
VALUES(?,?)") if err != nil { panic(err.Error()) 
} 
insForm.Exec(name, city) 
log.Println("INSERT: Name: " + name + " | City: " + city) 
} 
defer db.Close() 
http.Redirect(w, r, "/", 301) 
} 
 func Update(w http.ResponseWriter, r *http.Request) { db := dbConn() if r.Method == "POST" { name := r.FormValue("name") city := r.FormValue("city") id := r.FormValue("uid") 
insForm, err := db.Prepare("UPDATE Employee SET name=?, city=? WHERE id=?") 
if err != nil { panic(err.Error()) 
} 
insForm.Exec(name, city, id) 
log.Println("UPDATE: Name: " + name + " | City: " + city) 
} 
defer db.Close() 
http.Redirect(w, r, "/", 301) 
} 
func Delete(w http.ResponseWriter, r *http.Request) { db := dbConn() 
emp := r.URL.Query().Get("id") 
delForm, err := db.Prepare("DELETE FROM Employee WHERE id=?") if err != nil { panic(err.Error()) 
} delForm.Exec(emp) log.Println("DELETE") defer db.Close() 
http.Redirect(w, r, "/", 301) 
} 
 func main() { log.Println("Server started on: http://localhost:8080") http.HandleFunc("/", Index) http.HandleFunc("/show", Show) http.HandleFunc("/new", New) http.HandleFunc("/edit", Edit) http.HandleFunc("/insert", Insert) http.HandleFunc("/update", Update) http.HandleFunc("/delete", Delete) http.ListenAndServe(":8080", nil) } 
 
{{ define "Index" }} 
{{ template "Header" }} 
{{ template "Menu" }} 
<h2> Registered </h2> 
<table border="1"> 
<thead> 
<tr> 
<td>ID</td> 
<td>Name</td> 
<td>City</td> 
<td>View</td> 
<td>Edit</td> 
<td>Delete</td> 
</tr> 
</thead> 
<tbody> 
{{ range . }} 
<tr> 
<td>{{ .Id }}</td> 
<td> {{ .Name }} </td> 
<td>{{ .City }} </td> 
<td><a href="/show?id={{ .Id }}">View</a></td> 
<td><a href="/edit?id={{ .Id }}">Edit</a></td> 
<td><a href="/delete?id={{ .Id }}">Delete</a><td> </tr> 
{{ end }} 
</tbody> 
</table> 
{{ template "Footer" }} 
{{ end }} 
{{ define "Header" }} 
<!DOCTYPE html> 
<html lang="en-US"> 
<head> 
<title>Golang Mysql Curd Example</title> 
<meta charset="UTF-8" /> 
</head> 
<body> 
<h1>Golang Mysql Curd Example</h1> 
{{ end }} 
{{ define "Footer" }} </body> 
</html> 
{{ end }} 
{{ define "Menu" }} 
<a href="/">HOME</a> | 
<a href="/new">NEW</a> 
{{ end }} 
{{ define "Show" }} 
{{ template "Header" }} 
{{ template "Menu" }} 
<h2> Register {{ .Id }} </h2> 
<p>Name: {{ .Name }}</p> 
<p>City: {{ .City }}</p><br /> <a href="/edit?id={{ .Id 
}}">Edit</a></p> 
{{ template "Footer" }} 
{{ end }} 
{{ define "New" }} 
{{ template "Header" }} 
{{ template "Menu" }} 
<h2>New Name and City</h2> 
<form method="POST" action="insert"> 
<label> Name </label><input type="text" name="name" /><br /> 
<label> City </label><input type="text" name="city" /><br /> 
<input type="submit" value="Save user" /> </form> 
{{ template "Footer" }} 
{{ end }} 
{{ define "Edit" }} 
{{ template "Header" }} 
{{ template "Menu" }} 
<h2>Edit Name and City</h2> 
<form method="POST" action="update"> 
<input type="hidden" name="uid" value="{{ .Id }}" /> 
<label> Name </label><input type="text" name="name" value="{{ 
.Name }}" /><br /> 
<label> City </label><input type="text" name="city" value="{{ 
.City }}" /><br /> 
<input type="submit" value="Save user" /> 
</form><br /> 
{{ template "Footer" }} 
{{ end }} 







week-12


package main import ( 
"fmt" 
"strings" 
) 
 func main() { fmt.Println(strings.ContainsAny("Germany", "G")) fmt.Println(strings.ContainsAny("Germany", "g")) 
 fmt.Println(strings.Contains("Germany", "Ger")) fmt.Println(strings.Contains("Germany", "ger")) fmt.Println(strings.Contains("Germany", "er")) 
 fmt.Println(strings.Count("cheese", "e")) 
 fmt.Println(strings.EqualFold("Cat", "cAt")) fmt.Println(strings.EqualFold("India", "Indiana")) 
 
 
} 



week-11

package main 
import ( 
"fmt" 
"sort" 
) 
func main() { 
 fmt.Println("Interger Reverse Sort") num := []int{50,90, 30, 10, 50} sort.Sort(sort.Reverse(sort.IntSlice(num))) fmt.Println(num) 
 fmt.Println() 
 fmt.Println("String Reverse Sort") 
text := []string{"Japan","UK","Germany","Australia","Pakistan"} sort.Sort(sort.Reverse(sort.StringSlice(text))) fmt.Println(text) 
 
} 


week-10

package main import "fmt" 
// function to remove duplicate values func removeDuplicates(s []string) []string { 
 	bucket := make(map[string]bool)  	var result []string  	for _, str := range s { 
 if _, ok := bucket[str]; !ok {  bucket[str] = true 
 	result = append(result, str) 
 	} 
 	} 
 	return 
 	result 
} 
func main() { 
 
// creating an array of strings 
array := []string{"abc", "cde",  "efg",  "efg", "abc", "cde"} fmt.Println("The given array of string is:", array) fmt.Println() 
 
// calling the function result := removeDuplicates(array) 
fmt.Println("The array obtained after removing the duplicate entries 
is:", result) 
} 


week-8

package main 
import ( 
"html/template" 
"net/http" 
) 
 type ContactDetails struct { 
Email string 
Subject string 
Message string 
} 
 func main() { tmpl := template.Must(template.ParseFiles("forms.html")) 
 http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) 
{ if r.Method != http.MethodPost { tmpl.Execute(w, nil) return 
} 
 details := ContactDetails{ 
Email: r.FormValue("email"), 
Subject: r.FormValue("subject"), 
Message: r.FormValue("message"), } 
 
// do something with details 
_ = details 
 tmpl.Execute(w, struct{ Success bool }{true}) }) 
 http.ListenAndServe(":8080", nil) 
} 
<!-- forms.html --> 
{{if .Success}} 
<h1>Thanks for your message!</h1> 
{{else}} 
<h1>Contact</h1> 
<form method="POST"> 
<label>Email:</label><br /> 
<input type="text" name="email"><br /> 
<label>Subject:</label><br /> 
<input type="text" name="subject"><br /> 
 
 
 
<label>Message:</label><br /> 
<textarea name="message"></textarea><br /> 
<input type="submit"> 
</form> 
{{end}} 



week-7


package main import "fmt" 
 
// start the function main () func main() { fmt.Println("Golang program to check for palindrome") 
 
// declare the variables 
 number	,	rem	,	temporary 
 reverse 	int 		= 	0 
varint 
var
 
// initialize the number variable  number = 45454 
	 temporary=number 	 
  
// For Loop used  for{ 	  rem = number%10  
	 	reverse = reverse*10 + rem 
	 	number /= 10 
if(number==0){ break // Break Statement used to exit from loop } } 
if(temporary==reverse){ fmt.Printf("Number %d is a Palindrome",temporary) 
}else{ fmt.Printf("Number %d is not a Palindrome",temporary) 
} 
// 


week-6

package main import "fmt" 
func main() { fmt.Print("Enter First String: ") //Print function is used to display output in same line 
var first string 	
fmt.Scanln(&first) 
user  fmt.Print("Enter Second String: ") var second string fmt.Scanln(&second) 	// Take input from 
fmt.Print(first + second) 	// Addition of two 
string } 


week-5

package main import "fmt" 
func main(){ var rows int var temp int = 1 fmt.Print("Enter number of rows : ") fmt.Scan(&rows) 
 for i := 1; i <= rows; i++ { for k := 1; k <= i; k++ { 
fmt.Printf(" %d",temp) temp++ } 
fmt.Println("") 
} 
 
} 
 

week-4

package main import ( 
"fmt" 
"math" ) func main(){ 
var num[10] float64 var sum,mean,sd float64 fmt.Println("****** Enter 10 elements *******") for i := 1; i <= 10; i++ { fmt.Printf("Enter %d element : ",i) fmt.Scan(&num[i-1]) sum += num[i-1] 
} mean = sum/10; 
for j := 0; j < 10; j++ { 
// The use of Pow math function func Pow(x, y float64) 
float64  
 	sd += math.Pow(num[j] - mean, 2) 
} 
// The use of Sqrt math function func Sqrt(x float64) float64 sd = math.Sqrt(sd/10) 
 fmt.Println("The Standard Deviation is : ",sd) } 





week-3


package main 
import ( parent "family/father" child "family/father/son" 
 
"fmt" 
) 
 func main() { f := new(parent.Father) 
fmt.Println(f.Data("Mr. Jeremy Maclin")) 
 c := new(child.Son) fmt.Println(c.Data("Riley Maclin")) 
 
} package father import "fmt" 
func init() { fmt.Println("Father package initialized") } 
 type Father struct { Name string 
} 
 func (f Father) Data(name string) string { 
f.Name = "Father : " + name return f.Name 
 
} 
 
 
 package son import "fmt" func init() { 
fmt.Println("Son package initialized") 
 
} 
 type Son struct { 
Name string 
} 
 func (s Son) Data(name string) string { 
s.Name = "Son : " + name 
return s.Name 
 
}  



week-2



package main import "fmt" func main() { var rows,k,temp,temp1 int fmt.Print("Enter number of rows :") fmt.Scan(&rows) 
 for i := 1; i <= rows; i++ { 
 for j := 1; j <= rows-i; j++ { fmt.Print(" ") 
temp++ 
}  for{  if( temp <= rows-1){ fmt.Printf(" %d",i+k) temp++ 
}else{ temp1++ 
fmt.Printf(" %d",(i+k-2*temp1)) 
} k++ 
 if(k == 2*i-1){ break 
} 
 
} temp = 0 temp1 = 0 k = 0 fmt.Println("") 
} 
 
} 



