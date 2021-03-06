# Dropdown In Vanilla JavaScript

#### Part-1

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vanilla Dropdown</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
            color: black;
        }        
    </style>
</head>
<body>
    <div class="dropdown closed">
        <h2 class="icon">Dropdown <span>>∆</span></h2>
        <ul class="menu">
            <li><a href="#">Item 1</a></li>
            <li><a href="#">Item 2</a></li>
            <li><a href="#">Item 3</a></li>
            <li><a href="#">Item 4</a></li>
        </ul>
    </div>
</body>
</html>
```



#### Part-2 - Design Dropdown layout

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vanilla Dropdown</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }

        html, body {
            font-size: 62.5%;
        }
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
            color: black;
        }        

        .dropdown {
            transition: all 0.2s ease-in-out;
            overflow: hidden;
            margin: 30px;
            background: rgb(248, 248, 248);
            border: solid 1px rgb(222, 222, 222);
            width: 320px;
            cursor: pointer;
        }

        .icon {
            display: flex;
            justify-content: space-between;
            padding: 2rem;
            font-size: 3rem;
        }

        .menu {
            height: 240px;
        }

        .menu li {
            font-size: 24px;
            text-transform: uppercase;
            padding: 14px 10px;
            border-top: solid 1px rgb(202, 202, 202);
        }
    </style>
</head>
<body>
    <div class="dropdown closed">
        <h2 class="icon">Dropdown <span>∆</span></h2>
        <ul class="menu">
            <li><a href="#">Item 1</a></li>
            <li><a href="#">Item 2</a></li>
            <li><a href="#">Item 3</a></li>
            <li><a href="#">Item 4</a></li>
        </ul>
    </div>
</body>
</html>
```



#### Part-3 - Adding An Event Listener

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vanilla Dropdown</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }

        html, body {
            font-size: 62.5%;
        }
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
            color: black;
        }        

        .dropdown {
            transition: all 0.2s ease-in-out;
            overflow: hidden;
            margin: 30px;
            background: rgb(248, 248, 248);
            border: solid 1px rgb(222, 222, 222);
            width: 320px;
            cursor: pointer;
        }

        .icon {
            display: flex;
            justify-content: space-between;
            padding: 2rem;
            font-size: 3rem;
        }

        .menu {
            height: 240px;
        }

        .menu li {
            font-size: 24px;
            text-transform: uppercase;
            padding: 14px 10px;
            border-top: solid 1px rgb(202, 202, 202);
        }
        
        .dropdown.closed .menu {
            height: 0px;
        }
        
        .dropdown.closed .icon span {
            transform: rotate(180deg);
        }
        
    </style>
</head>
<body>
    <div class="dropdown closed">
        <h2 class="icon">Dropdown <span>∆</span></h2>
        <ul class="menu">
            <li><a href="#">Item 1</a></li>
            <li><a href="#">Item 2</a></li>
            <li><a href="#">Item 3</a></li>
            <li><a href="#">Item 4</a></li>
        </ul>
    </div>
    
    <script>
      let dropdown = document.querySelector('.dropdown');
      
      dropdown.addEventListener('click', (e) => {
          if (dropdown.classList.contains('closed')) {
              dropdown.classList.remove('closed');
          } else {
              dropdown.classList.add('closed');
          }
      })
    </script>
</body>
</html>
```



#### Part-4 Extra Style + mouseenter + mouseleave Version

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vanilla Dropdown</title>
    <style>
        * {
            padding: 0;
            margin: 0;
            box-sizing: border-box;
        }

        html, body {
            font-size: 62.5%;
        }
        
        ul {
            list-style: none;
        }
        
        a {
            text-decoration: none;
            color: black;
        }        

        h2 {
            font-size: 3rem;
        }

        .dropdown {
            transition: all 0.2s ease-in-out;
            overflow: hidden;
            margin: 30px;
            background: rgb(248, 248, 248);
            border: solid 1px rgb(222, 222, 222);
            width: 320px;
            cursor: pointer;
            display: grid;
            grid-template-columns: 1fr;
            grid-template-rows: 1fr;
            grid-template-areas:
                "icon"
                "menu";
        }
        
        .dropdown.closed {
            grid-area: icon;
        }
        
        .icon {
            display: flex;
            justify-content: space-around;
            padding: 2rem;
            font-size: 3rem;
        }
        
        .icon span {
            transition: all 0.2s ease-in-out;
            transform: rotateX(180deg) rotateY(180deg);
  			color: rgb(252, 102, 102);
        }
        
        .closed .icon span {
            transform: rotateX(0deg);
            color: black;
        }

        .menu {
            height: 290px;
            transition: all 0.2s ease-in-out;
            grid-area: menu;
        }

        .menu li {
            font-size: 24px;
            text-transform: uppercase;
            padding: 14px 10px;
            border-top: solid 1px rgb(202, 202, 202);
            transition: all 0.2s ease-in-out;
        }
        
        .menu li:hover {
            background: rgb(252, 102, 102);
        }
        
        .menu li:hover a {
            color: white;
        }
        
        .dropdown.closed .menu {
            height: 0px;
        }
        
        #output {
            position: absolute;
            right: 20px;
            top: 30px;
            background: rgb(242, 242, 242);
            padding: 1rem;
            width: 350px;
            border: solid 1px rgb(222, 222, 222);  
        }
        
        @media all and (max-width: 800px) {
            #output {
                display: none;
            }
        }
        
    </style>
</head>
<body>
    <div class="dropdown closed">
        <h2 class="icon">Dropdown <span>∆</span></h2>
        <ul class="menu">
            <li><a href="#">Select This Option</a></li>
            <li><a href="#">Choose Something Else</a></li>
            <li><a href="#">Get Help</a></li>
            <li><a href="#">Contact Us Today</a></li>
        </ul>
    </div>
    
    <div id="output">
        <h2>State: <span id="status"></span></h2>
    </div>
    
    <script>
      let dropdown = document.querySelector('.dropdown');
      let status = document.querySelector('#status');
      
      dropdown.addEventListener('mouseenter', (e) => {
          if (dropdown.classList.contains('closed')) {
              dropdown.classList.remove('closed');
              status.innerHTML = 'OPEN';
          } 
      });

      dropdown.addEventListener('mouseleave', (e) => {
          if(!dropdown.classList.contains('closed')) {
              dropdown.classList.add('closed');
              status.innerHTML = 'CLOSED';
          }
      })
    </script>
</body>
</html>
```

https://www.jeffastor.com/blog/building-a-dropdown-menu-in-10-lines-of-javascript



