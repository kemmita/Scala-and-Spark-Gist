1. We want to get the mean salary from our table and store that in a local constant.
```sc
val ms = df5.select(mean("salaryFloat")).collect

val ms_ = ms(0)(0)

val ms_string = ms_.toString

val ms_value = ms_string.toFloat
```
