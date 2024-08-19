# Chapter 6 - Attributes
 
1. src Attribute

```
<img src="image.jpg" alt="A beautiful image">

<script src="script.js"></script>
```

2. href Attribute

```
<a href="https://www.example.com">Visit Example.com</a>
```

3. alt Attribute

```
<img src="image.jpg" alt="A beautiful image">
```

4. width and height Attributes

```
<img src="image.jpg" width="200" height="150" alt="A smaller image">

<canvas width="400" height="300"></canvas>
```

5. for Attribute

```
<label for="username">Username:</label>

<input type="text" id="username" name="username">
```

6. type Attribute

```
<input type="text" id="username" name="username">

<input type="checkbox" id="subscribe" name="subscribe">
```

7. rows and cols Attributes

```
<textarea id="comments" name="comments" rows="4" cols="50"></textarea>
```

8. action and method Attributes

```
<form action="/submit" method="post">
    <!-- Form elements here -->
</form>
```

9. controls Attribute

```
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio tag.
</audio>

<video controls>
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>
```

10. disabled Attribute

```
<input type="text" id="disabledInput" name="disabledInput" disabled>

<button type="button" disabled>Disabled Button</button>
```

11. video poster attribute

```
<video width="320" height="240" poster="/images/thumbnail.jpg" controls>
   <source src="movie.mp4" type="video/mp4">
   <source src="movie.ogg" type="video/ogg">
   Your browser does not support the video tag.
</video>
```