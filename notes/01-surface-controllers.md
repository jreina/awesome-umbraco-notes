# Surface Controllers

## Intro
This is a basic intro to surface controllers

_a site is more than just displaying data_

> a surface controller is an MVC controller that interacts with the front-end rendering of an Umbraco page.

You'll need a bit of MVC knowledge.

A surface controller is used to render child action content and handle form data submission. A regular ASP.Net MVC controller, but inherits from `Umbraco.Web.Mvc.SurfaceController`. By inheriting, it is auto-routed and has instant access to Umbraco helper methods and properties.

## Creating the model
- model is the data we'll be working with
- model is a POCO
- model is data passed between view and controller

## Setting up the view

- view controls markup
- partial view. only the markup for the form
- create strongly typed view for better intellisense

create partial view in ~/Views/Partials/
use MVC input extension methods (Html.TextBoxFor)

## The surface controller

- Append "SurfaceController" to name of controller _by convention_
- Create as empty controller
- Always inherit from `Umbraco.Web.Mvc.SurfaceController`

## Handling posts
We need to:
- Update controller with a method to handle posts
- Update view to post to correct method.

### Adding post-handling method
Add new method to surface controller, returning an `ActionResult`. Add the `[HttpPost]` attribute to this new method to ensure that is can only do posts. This method should also accept a single parameter that is the same type as your model. 

### Posting to correct method
Use `Html.BeginUmbracoForm` and use the type of your surface controller as the single type argument. The name of your method should be used as the `action` argument here.

We should now be posting to the correct method on our surface controller from our view.
