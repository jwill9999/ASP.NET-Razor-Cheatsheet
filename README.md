# ASP.NET Razor - C# Code Syntax - [PDF Download Cheatsheet](https://1drv.ms/b/s!Ai0GNI50Q5GAgdQ0B2b3gDPlXcxM_w)

<div align="center">
<img src="https://vietsang.club/wp-content/uploads/2018/10/ASP.Net8_-1.png" width=100%/>
</div>

<br>
<br>
<br>

# Index<br>

[Razor Comments](#Razor-Comments)<br>
[Inline expression](#Inline-expression)<br>
[Multi-statement block](#Multi-statement-block)<br>
[Store String](#Store-Date)<br>
[Store Date](#Tag-Helpers)<br>
[Store Date](#Tag-Helpers)<br>
[Variables](#Variables)<br>
[Convert Data Types ](#Convert-Data-Types )<br>
[Loops](#Loops)<br>
[Arrays](#Arrays)<br>
[Conditionals](#Conditionals)<br>
[Using](#Using)<br>
[Models View](#Models-View)<br>
[Dependency Injection](#Dependency-Injection)<br>
[Add Functions](#Add-Functions)<br>
[Create Templates ](#Create-Templates )<br>
[Conditional Attributes](#Conditional-Attributes)<br>
[Forms](#Forms)<br>
[Add Partials](#Add-Partials)<br>
[Add link to a page](#Add-link-to-a-page)<br>
[ Loop through a list and output](#Loop-through-a-list-and-output)




### Razor is a markup syntax that lets you embed server-based code (Visual Basic and C#) into web pages

## Razor Comments

```c#
@*  A one-line code comment. *@

@*
    This is a multiline code comment.
    It can continue for any number of lines.
*@
```
```c#
@{
    @* This is a comment. *@
    var theVar = 17;
}
```

<br>

[back to top](#Index)<br>

<br>

## Single statement block

```c#
@{ var myMessage = "Hello World"; }
```

## Inline expression

```c#
@{ var myMessage = "Hello World"; }
```
## Multi statement block

```c#
@{
var greeting = "Welcome to our site!";
var weekDay = DateTime.Now.DayOfWeek;
var greetingMessage = greeting + " Here in Huston it is: " + weekDay;
}
<p>The greeting is: @greetingMessage</p> }
```

<br>

[back to top](#Index)<br>

<br>

## Store String 

```c#
/* A string is a sequence of characters that are treated as text. To specify a string, you enclose it in double quotation marks:*/

@{ var welcomeMessage = "Welcome, new members!"; }
<p>@welcomeMessage</p>
```
## Store Date 

```c#
@{ var year = DateTime.Now.Year; }
```

<br>

[back to top](#Index)<br>

<br>

## Read User Input

```c#
@{
var totalMessage = "";
if(IsPost)
    {
    var num1 = Request["text1"];
    var num2 = Request["text2"];
    var total = num1.AsInt() + num2.AsInt();
    totalMessage = "Total = " + total;
}
}

```

<br>

[back to top](#Index)<br>

<br>

## Variables

```c#
@{
    // Assigning a string to a variable.
    var greeting = "Welcome!";

    // Assigning a number to a variable.
    var theCount = 3;

    // Assigning an expression to a variable.
    var monthlyTotal = theCount + 5;

    // Assigning a date value to a variable.
    var today = DateTime.Today;

    // Assigning the current page's URL to a variable.
    var myPath = this.Request.Url;

    // Declaring variables using explicit data types.
    string name = "Joe";
    int count = 5;
    DateTime tomorrow = DateTime.Now.AddDays(1);
}

```

### Display Variables

```c#
@{
    // Embedding the value of a variable into HTML markup.
    <p>@greeting, friends!</p>

    // Using variables as part of an inline expression.
    <p>The predicted annual total is: @( monthlyTotal * 12)</p>

    // Displaying the page URL with a variable.
    <p>The URL to this page is: @myPath</p>
}

```


<br>

[back to top](#Index)<br>

<br>

## Convert Data Types 


| Method     | Description          |Examples  |
| ------------- |:-------------:| -----:|
|AsInt(),<br> IsInt() |   Converts a string to an integer.   | ``` if (myString.IsInt())```<br>  ```{myInt=myString.AsInt();```|   
|AsFloat(), IsFloat()| Converts a string to a floating-point number.|```if (myString.IsFloat())```<br>```{myFloat=myString.AsFloat();}```|
|AsDecimal(), IsDecimal()| Converts a string to a decimal number..|```if (myString.IsDecimal())```<br>```{myDec=myString.AsDecimal();}```|
|AsDateTime(), IsDateTime()|Converts a string to an ASP.NET DateTime type.| ```myString="10/10/2012";```<br>``` myDate=myString.AsDateTime();```|
|AsBool(),<br> IsBool()|Converts a string to a Boolean..| ```myString="True";```<br> ```myBool=myString.AsBool();```|
|ToString()|Converts any data type to a string.| ```myInt=1234;```<br> ```myString=myInt.ToString();```|

### Coverting Data Types example

```c#
@{
    var total = 0;

    if(IsPost) {
        // Retrieve the numbers that the user entered.
        var num1 = Request["text1"];
        var num2 = Request["text2"];
        // Convert the entered strings into integers numbers and add.
        total = num1.AsInt() + num2.AsInt();
    }
}

```

<br>

[back to top](#Index)<br>

<br>

# Loops

## Standard Loop

```c#
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <text>Name: @person.Name</text>
}
```

  

## ForEach Loops 

```c#
<ul>
@foreach (var myItem in Request.ServerVariables)
{
    <li>@myItem</li>
}
</ul>
```
## While Loops 

```c#
@{
    var countNum = 0;
    while (countNum < 50)
    {
        countNum += 1;
        <p>Line #@countNum: </p>
    }
}
```


<br>

[back to top](#Index)<br>

<br>

## Arrays 

```c#
@{
string[] members = {"Jani", "Hege", "Kai", "Jim"};
int i = Array.IndexOf(members, "Kai")+1;
int len = members.Length;
string x = members[2-1];
}
<html>
<body>
<h3>Members</h3>
@foreach (var person in members)
{
<p>@person</p>
}
<p>The number of names in Members are @len</p>
<p>The person at position 2 is @x</p>
<p>Kai is now in position @i</p>
</body>
</html>
```


<br>

[back to top](#Index)<br>

<br>


# Conditionals

## If 

```c#
@{
  var showToday = true;
  if(showToday)
  {
    @DateTime.Today;
  }
}
```
## If Else 

```c#
@{
  var showToday = false;
  if(showToday)
  {
    @DateTime.Today;
  }
  else
  {
    <text>Sorry!</text>
  }
}
```
## Else If 

```c#
@{
    var theBalance = 4.99;
    if(theBalance == 0)
    {
        <p>You have a zero balance.</p>
    }
    else if (theBalance  > 0 && theBalance <= 5)
    {
        <p>Your balance of $@theBalance is very low.</p>
    }
    else
    {
        <p>Your balance is: $@theBalance</p>
    }
}
```
## Switch Statement 

```c#
@{
    var weekday = "Wednesday";
    var greeting = "";

    switch(weekday)
    {
        case "Monday":
            greeting = "Ok, it's a marvelous Monday";
            break;
        case "Tuesday":
            greeting = "It's a tremendous Tuesday";
            break;
        case "Wednesday":
            greeting = "Wild Wednesday is here!";
            break;
        default:
            greeting = "It's some other day, oh well.";
            break;
    }

    <p>Since it is @weekday, the message for today is: @greeting</p>
}
```
## Try Catch Finally

```c#
@try
{
    throw new InvalidOperationException("You did something invalid.");
}
catch (Exception ex)
{
    <p>The exception message: @ex.Message</p>
}
finally
{
    <p>The finally statement.</p>
}

```


<br>

[back to top](#Index)<br>

<br>


## Using 

```c#

/* The @using directive adds the C# using directive to the generated view:*/

@using System.IO
@{
    var dir = Directory.GetCurrentDirectory();
}
<p>@dir</p>

```

<br>

[back to top](#Index)<br>

<br>


## Models View

```c#
// The @model directive specifies the type of the model passed to a view:

@model TypeNameOfModel

```

## Access Model 

```html
<div>The Login Email: @Model.Email</div>
```

## Dependency Injection

```c#
@inject +ServiceName
```

<br>

[back to top](#Index)<br>

<br>

## Add Functions

```html
@functions {
    public string GetHello()
    {
        return "Hello";
    }
}

<div>From method: @GetHello()</div>

```

<br>

[back to top](#Index)<br>

<br>

## Create Templates 

Create a class

```c#
public class Pet
{
    public string Name { get; set; }
}
```

create a .```cshtml``` page

```html
@{
    Func<dynamic, object> petTemplate = @<p>You have a pet named @item.Name.</p>;

    var pets = new List<Pet>
    {
        new Pet { Name = "Rin Tin Tin" },
        new Pet { Name = "Mr. Bigglesworth" },
        new Pet { Name = "K-9" }
    };

     <!-- The template is rendered with pets supplied by a foreach statement: -->

     @foreach (var pet in pets)
{
    @petTemplate2(pet)
}
}

```

Rendered output

```html
<p>You have a pet named <strong>Rin Tin Tin</strong>.</p>
<p>You have a pet named <strong>Mr. Bigglesworth</strong>.</p>
<p>You have a pet named <strong>K-9</strong>.</p>
```

<br>

[back to top](#Index)<br>

<br>

## Conditional Attributes

```html
@{
    string divStyle = null;
    if(Request.QueryString["style"] != null)
    {
        divStyle = "background-color: yellow;";
    }
}
<div style="@divStyle">Hello, world!</div>
```


<br>

[back to top](#Index)<br>

<br>

## Forms

```html
<form method="post">
            <div asp-validation-summary="ModelOnly" class="text-danger"></div>
            <div class="form-group">
                <label asp-for="Movie.Title" class="control-label"></label>
                <input asp-for="Movie.Title" class="form-control" />
                <span asp-validation-for="Movie.Title" class="text-danger"></span>
            </div>
            <div class="form-group">
                <label asp-for="Movie.ReleaseDate" class="control-label"></label>
                <input asp-for="Movie.ReleaseDate" class="form-control" />
                <span asp-validation-for="Movie.ReleaseDate" class="text-danger"></span>
            </div>           
            <div class="form-group">
                <input type="submit" value="Create" class="btn btn-default" />
            </div>
</form>

```

<br>

[back to top](#Index)<br>

<br>


## Add Partials 

```js
@section Scripts {
    @{await Html.RenderPartialAsync("_ValidationScriptsPartial");}
}
```

<br>

[back to top](#Index)<br>

<br>

## Add link to a page

```html
<div>
    <a asp-page="./Index">Back to List</a>
</div>
```

<br>

[back to top](#Index)<br>

<br>

## Loop through a list and output

```html
<tbody>
        @foreach (var item in Model.Movie)
        {
            <tr>
                <td>
                    @Html.DisplayFor(modelItem => item.Title)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.ReleaseDate)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.Genre)
                </td>
                <td>
                    @Html.DisplayFor(modelItem => item.Price)
                </td>
                <td>
                    <a asp-page="./Edit" asp-route-id="@item.ID">Edit</a> |
                    <a asp-page="./Details" asp-route-id="@item.ID">Details</a> |
                    <a asp-page="./Delete" asp-route-id="@item.ID">Delete</a>
                </td>
            </tr>
        }
    </tbody>

```


<br>

[back to top](#Index)<br>

<br>

