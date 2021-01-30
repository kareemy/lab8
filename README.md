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
  
  
