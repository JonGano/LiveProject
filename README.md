# LiveProject
This repository contains a description of the the .NET MVC stories completed during a sprint. They are discribed in order to better explain the entire proccess.
All of which are intended to create a blog photo section of the MVC program that is user friendly and mapped to a database.

# story 1: 
Involves creating a blog photo model with 3 properties: id(int,primary key), name(string) and photo(byte[])</br>
It represents all of the images that are used in the blog area.<br/>

![image](https://user-images.githubusercontent.com/97046218/164050315-bb5b06ea-9717-422f-9704-8c5d011134cd.png)

Once created, I used code first migration to create a table in the existing database that relates to all objects of this model </br>
From within Visual Studios I used Entity Framework to scaffold the crud pages for the model.</br>
(index,create,edit,details and delete pages)

![BlogPhotoDBTable](https://user-images.githubusercontent.com/97046218/164051315-a6e8123d-6afc-4e67-affd-1afe3210975a.png)

# story 2:
Once the CRUD pages were created, they needed to be styled. In this story I used external CSS from within the blog.css page to style the create and edit views.
These included styled submit and back buttons with hover effects, header and input container with border.</br>

![CreatePage](https://user-images.githubusercontent.com/97046218/164059676-c8453bcb-33fb-4731-b7a5-137746d49902.png)

![EditPage](https://user-images.githubusercontent.com/97046218/164059793-742eaeb1-7743-4120-984d-927d28bd631d.png)

# story 3:
On this story I worked on photo storage and retrieval by first creating an html input field on the create and edit views</br>
for the user to upload image files.  
![ImgFileFromViewPage](https://user-images.githubusercontent.com/97046218/164060320-87ab9956-0537-4b2c-8252-983573786d0f.png)
Given a unique Id/name for the input attribute, the blogPhoto Controller can then call on it as an argument for a method.</br>
In order for the view to pass it to the controller, the using statment at the top of the create and edit views must be changed from the following:</br>
![OrigionalActionLinkReference](https://user-images.githubusercontent.com/97046218/164061719-fad8086f-5479-40be-a433-9de5dcdeb767.png)

to:
![FromViewToController](https://user-images.githubusercontent.com/97046218/164061798-eb314941-f65b-41c1-b7dd-176d6967b314.png)
-
Once the blogPhoto Controller has access to the image file, I created a method that takes an image file as an argument and converts it to a byte[] for storage in the database</br>
![ImgToByte Method](https://user-images.githubusercontent.com/97046218/164062343-5b81b5e3-a014-40a8-a09a-59e0d8525b50.png)

The create and edit actionresult methods were then both given a parameter where the user's file from the view is taken.  I called on</br>
the previous method "convertPhoto()" passing in this image file and assigning this new byte[] to the newly created/edited blogPhoto object.
![CreateMethod](https://user-images.githubusercontent.com/97046218/164066231-d93326ef-f2ea-4096-ab7d-2a7d55fb288c.png)
 After the model of the new object is complete, it is added to the blogPhoto db table and then saved.
 
 Now the model is given to the index view and using a foreach loop, all photos saved in the database can be displayed on the index page.
![IndexView](https://user-images.githubusercontent.com/97046218/164067688-aa16491d-f6ab-4b3c-a9c9-1110c7089fef.png)

Within the foreach loop is a line of code that converts the byte[] to base 64 string so that the user sees the image instead of an array of numbers.</br>
![ConvertToBase64](https://user-images.githubusercontent.com/97046218/164068211-94409655-ea78-41f6-8074-deada3943201.png)
The above line utilizes viewbag so that this new string can be sent as the source to the html image tag below.
![AnchorTag](https://user-images.githubusercontent.com/97046218/164068671-8b45d158-28ca-4b07-ac02-82333e7ca798.png)
The image attribute is nested within an anchor<a> tag for the purpose of turning the displayed image into a link that when clicked on sends the user</br>
to the images details page.

# story 4:
This story calls for the index to be styled.  Using a combination of bootstrap and external CSS, I determined the </br>
size of the photos and how they were to appear on the page. Stacked in order of id and at a centered width on</br>
the screen using bottstrap card-column layout.
![blogPhotoIndexPage](https://user-images.githubusercontent.com/97046218/164070946-68f92986-9324-4a34-a666-7532171918c2.png)

When the cursor hovers over an image, the image expands, the title is shown in the top left corner and delete/edit</br>
bootstrap badge-pill buttons are shown in the bottom left of the image. Using the transition CSS property</br>
the image eases into what is seen below over two seconds. 
![IndexHoverEffect](https://user-images.githubusercontent.com/97046218/164071795-c7ab6064-1dac-4745-8930-83e824b016c2.png)

# story 5:
This final story calls for some styling to the details and delete pages.  With CSS I centered the photo, made it larger and gave the image a </br>
hover effect.  The font color and style was also changed.
![DeleteViewPage](https://user-images.githubusercontent.com/97046218/164073628-29fdbae6-1697-4d3c-a8f3-2b79dca49008.png)

Although there are no examples of CSS in this readme, there are a few in this repo if interested.

