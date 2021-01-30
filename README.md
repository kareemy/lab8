## Your Name:


# CIDM 3312 Lab 8: Razor Pages

## Task 0: Setting up your ASP.NET Core project
1. Open up VS Code. Create a new ASP.NET Core project using the `webapp` template with the following terminal command: `dotnet new webapp`
  
2. ASP.NET Core projects run in a web server, not the console. Click Debug => Start Without Debugging or CTRL+F5 to run the project. You can also type `dotnet run` and go to the web site manually.
  
3. Browse the web site in your web browser. The URL is http://localhost:5000/. The web site may have an invalid security certificate. Allow an exception for it.
  
## Task 1: Make some changes
1. In VS Code find the Index Razor Page (Index.cshtml) in the Pages folder. Modify the page so it displays "Welcome to CIDM 3312". Save the file.
  
2. Stop the web server and restart the ASP.NET Core project. Reload the page in your web browser to see the changes.

## Task 2: Studying Razor Pages
1. Look at `Index.cshtml` again. It contains a mixture of C# and HTML. The `@` sign is a special symbol. It indicates that the text following is either a special Razor Page keyword or C# Code.
    - `@page` => Required at the top of every Razor Page that identifies the page as a Razor Page.
    - `@model IndexModel` => Connects the Razor Page to a Page Model named IndexModel. The Page Model is in the file Index.cshtml.cs
    - `@{ ... }` => Everything inside these curly braces is C# code that will be executed on the server.
    - `ViewData["Title"] = "Home page";` => This is C# code that sets the page title. Where is this variable referenced? Look in `_Layout.cshtml`
   
2. The rest of `Index.cshtml` is HTML code. Notice this isn't a complete HTML page. The header, footer, and common navigation HTML code are in `_Layout.cshtml` and pulled in automaticallyed when the page is rendered.
    - Look in `_Layout.cshtml`. Find the `@RenderBody()` line. That is where the HTML code is inserted.
  
3. There is nothing to complete for this task, just familiarze yourself with Razor Pages.

## Task 3: Create your own Razor Page
1. Create a new Razor Page called `Time.cshtml` in the Pages folder with the following code:
      ```
      @page
      <div class="text-center">
        <p>Time: @DateTime.Now</p>
      </div>
      ```
    
2. Your Razor Page is called `Time.cshtml` so the URL is http://localhost:5000/Time. Run your app and refresh the page several times. Notice how the time keeps updating. 

## Task 4: Add your page to the layout
1. Go to `_Layout.cshtml` and add a link to `Time.cshtml` within the navigation area of the web site. See where it has HTML links for Home and Privacy - put HTML code there for your page.

2. Refresh the web site again and navigate to your Time page.

## Task 5: Add a Page Model
1. Create a Page Model called `Time.cshtml.cs` with the following code (You can copy from Index.cshtml.cs) Make sure to change the class name to TimeModel and namespace to match your project.
    ```
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Threading.Tasks;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.AspNetCore.Mvc.RazorPages;
    using Microsoft.Extensions.Logging;

    namespace lab8.Pages // Change the namespace to match your Index.cshtml.cs files namespace
    {
        public class TimeModel : PageModel
        {
            private readonly ILogger<IndexModel> _logger;

            public IndexModel(ILogger<IndexModel> logger)
            {
                _logger = logger;
            }

            public void OnGet()
            {

            }
        }
    }
    ```

2. Connect the Razor Page to the Page Model. How? Remember the `@model` keyword?

3. Within the Page Model create a string Property called Message and set it equal to some text.
    ```
    public class TimeModel : PageModel
    {
      public string Message {get; set;}
      
      public void OnGet()
      {
        Message = "Your Message Here";
      }
    }
    ```
 The method `OnGet()` is automatically called when there is a request for you page (specifically an HTTP GET request)
 
 4. Modify `Time.cshtml` so that it displays your message. Your message is a C# variable like `DateTime.Now` but it is part of the Page Model. You can access it with `@Model.Message`. Refresh the web page in your browser and take a look.
 
 ## Extra Credit Challenge Round: A more advanced model - Using a foreach loop
 1. Create a List of integers as a Property in the Page Model of `Time.cshtml.cs` called `LuckyNumbers`.
 
 2. Within the `OnGet()` method, initialize the list to a new list with a few lucky numbers.
 
 3. Razor Pages can really run most C# code. Write C# code in `Time.cshtml` to loop through every element of the list and display them with HTML. Use the `@` symbol to start your C# code. Good luck!
 
 4. Submit your assignment to GitHub.
  
  
