# Chapter 5 - Forms

1. Text Input

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="username">Username:</label>
        
        <input type="text" id="username" name="username" placeholder="Enter your username">

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](2.PNG)

![Image](3.PNG)

![Image](4.PNG)

5. Password Input

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="password">Password:</label>

        <input type="password" id="password" name="password" placeholder="Enter your password">

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](6.PNG)

![Image](7.PNG)

![Image](8.PNG)

9. Email Input

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="email">Email:</label>
        
        <input type="email" id="email" name="email" placeholder="Enter your email">

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](10.PNG)

![Image](11.PNG)

![Image](12.PNG)

![Image](13.PNG)


14. Number Input

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="quantity">Quantity:</label>

        <input type="number" id="quantity" name="quantity" min="1" max="10" step="1">

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](15.PNG)

![Image](16.PNG)

![Image](17.PNG)

![Image](18.PNG)

![Image](19.PNG)

![Image](20.PNG)

![Image](21.PNG)

![Image](22.PNG)

![Image](23.PNG)

![Image](24.PNG)


25. Checkbox

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="subscribe">Subscribe to newsletter:</label>

        <input type="checkbox" id="subscribe" name="subscribe" value="yes">

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](26.PNG)

![Image](27.PNG)

![Image](28.PNG)

29. Radio Buttons

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label>Gender:</label>
        
        <input type="radio" id="male" name="gender" value="male">
        
        <label for="male">Male</label>
        
        <input type="radio" id="female" name="gender" value="female">
        
        <label for="female">Female</label>

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](30.PNG)

![Image](31.PNG)

![Image](32.PNG)

34. Text Area

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="comments">Comments:</label>
        
        <textarea id="comments" name="comments" rows="4" cols="50" placeholder="Enter your comments"></textarea>

        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](35.PNG)

![Image](36.PNG)

![Image](37.PNG)

38. Select Dropdown

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="country">Country:</label>

        <select id="country" name="country">

            <option value="usa">United States</option>

            <option value="canada">Canada</option>

            <option value="uk">United Kingdom</option>

        </select>
        
        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](39.PNG)

![Image](40.PNG)

![Image](41.PNG)

![Image](42.PNG)

![Image](43.PNG)

44. File Upload

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="file">Upload a file:</label>

        <input type="file" id="file" name="file">
        
        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](45.PNG)

![Image](46.PNG)

![Image](47.PNG)

![Image](48.PNG)

49. Date Input

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>

    <form action="" method="get">

        <label for="birthdate">Birthdate:</label>

        <input type="date" id="birthdate" name="birthdate">
        
        <input type="submit" value="send">

    </form>
    
</body>
</html>
```

![Image](50.PNG)

![Image](51.PNG)

![Image](52.PNG)

![Image](53.PNG)