```sc
object ScalaDemo extends App
{
  // this func takes in two ints and returns a String
  val sumOfRes: (Int, Int) => String = (x: Int, y: Int) => {
    if((x+y) == 7) "Lucky" else "Looser"
  }
}
```
