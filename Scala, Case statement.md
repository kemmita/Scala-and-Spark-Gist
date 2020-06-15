```
val userRole = "Admin"                   
 	
userRole match {
 		case "Admin" => admin(userRole)
 		case "User" => println("User is a standard user")
 		case "Teacher" => println("User is a teahcer")
}                                        
 	
def admin(role: String): String = {
  return "Hello " + role
}

```
