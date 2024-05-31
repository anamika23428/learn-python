# _Pandas Series_


 A series is a Panda data structures that represents a one dimensional array-like object containing an array of data and an associated array of data type labels, called index.

## Creating a Series object:
***<name_of_your_series_object>=pd.Series(data)***

 

    import pandas as pd
    s1=pd.Series([4,5,2,3])
    print(s1)


output:

    0	4
    1	5
    2	2
    3	3
    dtype: int 64

**If the sequence passed to Series is a dictionary then the keys become index and values become data of the series object.** 
Eg:

    import pandas as pd
    s2=pd.Series({‘A’:1,’B’:2,’C’:3})
    Print(s2)

Output:

    A 1
    B 2
    C 3
    dtype: int 64

**If the data is scalar value, then the index argument to series() must be provided.**

## Additional Functionality
### 1. specifying NaN values:
* Sometimes you need to create a series object of a certain size but you do not have complete data available so in such cases you can fill missing data with a NaN(Not a Number) value. 
* When you store NaN value in series object, the data type must be floating pont type. even if you specify an integer type , pandas will promote it to floating point type automatically because NaN is not supported by integer type.

Eg: 

    import pandas as pd
    s3=pd.Series([1,np.Nan,2])
    print(s3)
output:

    0 1.0
    1 NaN
    2 2.0
    dtype: float64

### 2.specify Data Type and inde(es)as well as data with Series()
<series_object>=np.Series(data=None, index=None, dtype=None)

    import pandas as pd
    s4=pd.Series([1,2,3],index=['a','b','c'],dtype='float64')
    print(s4)
output:

    a    1.0
    b    2.0
    c    3.0
    dtype: float64

### 3. Expression to create data array 
<series_object>=np.Series(data=<function|expression>,index=None)

eg 1:

    import pandas as pd
    a=np.arange(1,5) # [1,2,3,4]
    s5=pd.Series(data=a**2,index=a)
    print(s5)
output:

    1 1
    2 4
    3 9
    4 16
    dtype: int64
eg 2:

    import pandas as pd
    a=[2,3] #list
    s6=pd.Series(data=(2*a))
    print(s6)
output:

    0    2
    1    3
    2    2
    3    3     * replicates the list twice
    dtype: int64

## Series object attribute
 
**Attribute**              |   **Description**
---|---
<series_object>.index      |    array of index of the series                     
<series_object>.values     |   array of values of the series                   
<series_object>.dtype      |    return dtype of the data                        
<series_object>.shape      |    return a tuple of the shape of the data         
<series_object>.ndim       |    return the number of dimensions of the data     
<series_object>.size       |    return number of elements in the data           
<series_object>.hasnans    |    retur True is there is any NaN in the data      
<series_object>.empty      |    return True if the series object is empty       
  
- If you use len() on a series object then it return total number of elements in the series object whereas <series_object>.count() return only the number of non NaN elements.

##  Accessing a series object and its elements
### 1.) Accessing individual element 
- <series_object>[< index >]    return the value of the element at the index.
- 'legal' indexes arte used to access individual element.
### 2.) Slicing 
- Irrespective of the indexes, the slices have been extracted position wise.
- Every individual element have position number starting from 0 onwards i.e 0 for 1st element and 1 for 2nd element ans so on.
- <series_object>[< start >:< end>] will return the values of the elements between the start and end position.

eg:

    import pandas as pd
    s7=pd.Series(data=[13,45,67,89],index=['A' ,'B' ,'C','D'])
    print(s7[:2])

output:

    A    13
    B    45
    dtype: int64


## Operation on series object

### Modifying elements and indexes 
*  <series_object>[indexes]=< new data value >
*  <series_object>[start : end]=< new data value >
*  <series_object>.index=[new indexes]

**Note: Series object are value-mutable but size immutable objects.**

### vector operations
**1.) <series_object> = <series_object> +/- < value >**

add/subtract the value to the series object.

**2.) <series_object> = <series_object>  * /(/) < value >**

multiply/divide the value with the series object

**3.) <series_object> = <series_object> ** < value >**

raise the series object to the power of the value

**4.) <series_object> = <series_object> % < value >**

return the remainder of the division of the series object with the value.

and many more like &(And), |(OR) etc.

### Arthmetic on series object
**1.) <series_object> +/-<series_object>**

 return the sum/subtract of the two series objects

**2.) <series_object> * /(/)<series_object>**

return the product/division of the two series objects.

Here one thing we should keep in mind that both the series object should have same indexes otherwise it will return NaN value to all the indexes of two series object .


### head() and tail() functions
**<series_object>.head(n)**

return the first n elements of the series object

**<series_object>.tail(n)**

return the last n elements of the series object

If you dont provide any value to n the by default it give results for n=5.
#### Few extra functions:
* <series_object>.sort_values()    return the series object in ascending order of the values.
* <series_object>.sort_index()    return the series object in ascending order of the index.
* <series_object>.sort_drop(<index_to_remove>)    return the series with the  deleted index that you removed and corresponding value.


