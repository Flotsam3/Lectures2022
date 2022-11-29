# 🔵 PROGRAMMING BASICS (PBA)


## <u>FORMS</u>

    const inputs = document.getElementById("my-form").elements;
    const inputByIndex = inputs[0];
    const inputByName = inputs["username"];
    const inputByNameAlt = inputs.username;

# 🔵 SINGLE PAGE APPLICATION (SPA)

Solution when javaScript is used in the script tag, in order to prevent js beeing loaded before the DOM

    addEventListener('DOMContentLoaded', (event) => {});


## File structuring

- src folder | main folder for all files

## <u>package.json</u>
create a new package.json (-y to skip prompts)

    npm init | npm init -y
- package name | name for the app
- version | starting withh 0.1
- description | infos to the app
- entry point | skip
- test commmand | skip
- git respository | skip
- keywords |
- author |
- license | ISC
  
#### dependencies

- dependencies | necessary other packeges to run our package
- node_modules | contains all necessary folders

## <u>node package manager (npm)</u>

- npmjs.com | homepage

### install a package
--save installs explicitly to the dependencies section

    npm i <name> | npm install --save <name>

## <u>node package manager (npm)</u>

- packs many different js files into one js file
- npm install webpack webpack-cli
- dist/main.js

## scripts inside package.json
- build script
  
        "build": "webpack"

- watch script
  
        "watch": "webpack --watch"

- running scripts
  
        npm run <script-name>

## webpack.config.js (in main folder)
    module.exports = {
        mode: "development"
    }

----

## Asynchronous code - 

## <u> PROMISES </u>
    function kochen(){
        const kochMeldet = Match.random() > 0.5;
        return new Promise((resolve, reject)=>{
            console.log("kochen");
            if (kochMeldet === true){
                resolve("zubereitetes Gericht");
            } else {
                reject("Gericht nicht zubereitet")
            }
        })
    }

    kochen().then((gericht)=>{
        console.log("servieren", gericht)
    }).catch(()=>{
        console.log("nicht servieren")
    }).finally(()=>{
        console.log("der Koch hat gesprochen")
    })

three stages of promise:
- pending
- resolved
- rejected

## <u>ASYNC AWAIT</u>

await is only working in an async function

    async function handleNumbers(number){
        const value = await isZero(0);
    }

    try {
        const p1 = method1();
        const p2 = method2();
  
        await Promise.all([p1, p2]);
    } 
    catch (error) {
        console.log(e);
    }

-------

## <u>FETCH</u>

  readable stream before using response.json()

### fetch with nested then

    fetch("https://swapi.de/api/people/8")
    .then((response)=>{
        console.log(response.status);
        if (response.status === 200){
            response.json().then((result)=>{
                console.log(result);
            })
        } else {
            throw new Error("Kein Character gefunden");
        }
    })

### fetch with chained then

    fetch("https://swapi.de/api/people/8")
    .then((response)=>{
        console.log(response.status);
        if (response.status === 200){
            return response.json()
        } else {
            throw new Error("Kein Character gefunden");
        }
    }).then((result)=>{
            console.log(result);
    }).catch((err)=>{
        console.log(err);
    })

### fetch with async await

    const getCharacter = async ()=>{
        try {
            const response = await fetch("https://swapi.de/api/people/8");
            if (response.status === 200){
            const result = await response.json();
            consle.log(result);
            } else {
                throw new Error("Kein Character gefunden");
            }
        } catch (error) {
            console.log(error)
        }

    }

    getCharacter();


## POST request

    const postCharacter = async ()=>{
        try {
            const response = await fetch(".../profile", {
                method: "POST",
                body: JSON.stringify({name: "Lightning Man"})
            })
            if (response.status !== 201){
                throw new Error("POST war nicht erfolgreich")
            }
        } catch(err) {
            console.log(error);
        }
    }

----

## LOCAL STORAGE / SESSION STORAGE

    const designMode = window.localStorage.getItem("designMode");
    const newDesignMode = designMode === "dark" ? "light" : "dark";

    window.localStorage.setItem("designMode", newDesignMode)

    getTaskList = JSON.parse(window.localStorage.getItem("task")) || [];
    window.localStorage.setItem("task", JSON.stringify(getTaskList));

----
## Website for generating testdata

[Mockaroo](https://mockaroo.com)


## Create a testserver with json-server

    npm i -g json-server

Run the testserver (-p flag for port is optional)

    json-server -p4001 <filename>

<br> 

---- 

<br>

- Framework (mehrere vorgefertigte Systeme, wie ein feststehendes Fachwerkhaus, man hat einen festgelegten Rahmen mit dem man arbeitet - Angular. Vue ist zwischen Angular und React)
- Library (man holt sich viele kleine Bausteine und setzt die zusammen - React)

 <img src="../../../../Downloads/react-skizze.png" style="width:800px;" />

  
## <u>REACT</u>
<br>

- create react app
- npx - executes a package instead of installing
-     npx create-react-app <name>
-     npm start
  

- src/App.js
- src/index.js (initialisation of the react app)
- public/index.html (html to be delivered)
  


        import logo from "./logo.svg"
        <img src={logo} />

- looping over arrays in jsx

        data.map((element, index)=>(
            <li key={index}>{element}</li>
        ))

### <u>Function component</u>



- in component

        function Navigation(){
            return (
                <nav>
                    <ul>
                        <li></li>
                        <li></li>
                        <li></li>
                    </ul>
                </nav>
            );
        }

- in index.js

        export default Navigation;


        import Navigation from "./components/Navigation";

        <React.StrictMode>
            <Navigation />
        </React.StrictMode>


### Props

    navLabel="Link 1"
    {props.navLabel}


## React manual installation

- npm init
- npm install react react-dom react-scripts
- creating a .gitignore file with following content:
  - /node_modules
- create src folder inside:
  - index.js - inside:
  
```
    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from ".App";
    const root = ReactDOM.createRoot(document.getElementById("root"));

    root.render(
        <React.StrictMode>
        </React.StrictMode>
    )
```
  - App.js - inside:


```
function App(){
        return (<div className="App">
    <h1>Hello World</h1>
    </div>
      )
    }
  - export default App

- create public folder inside:
  - index.html
  <div id="root"></div>
```

---------------

## <u>useState hook</u>

```
import {useState} from "react";
const [message, setMessage] = useState(false);
```

## <u>useEffect hook</u>
1. mounting
```
useEffect(()=>{
    console.log("Log when component mounts")
}, [])
```
2. updating
```
useEffect(()=>{
    console.log("Log when counter is updated")
}, [counter])
```
3. unmounting
``` js
useEffect(() => ()=> {
    console.log("Log when component will unmount")
}, [])

```

## <u>Styles components</u>

Inline styling
``` js
    const imgStyle = {
        width: 500
    }

    const h3Style = {
        fontSize: "25px"
    }

    <h3 style={h3Style}>{food.name}</h3>
    <img style={imgStyle} src={food.img}></img>
```

## <u>Styling with classes</u>

``` js
    import "./Food.css"

    const h3Style = {
        fontSize: "25px"
    }

    <h3 style={h3Style}>{food.name}</h3>
    <img className="food-img" src={food.img}></img>
```

## <u>SCSS in React</u>

    npm install sass

## <u>Bootstrap with React</u>

react-bootstrap.git

    npm install react-bootstrap bootstrap

index.js

    import "bootstrap/dist/css/bootstrap.min.css"

in App.js

    import button from "react-bootstrap/Button"

    <Button variant="primary">Filtern</Button>

bootstrap grid system

    import Container from 'react-bootstrap/Container';
    import Row from 'react-bootstrap/Row';
    import Col from 'react-bootstrap/Col';

```js
const foodContainer = favoriteFood.map((el, index)=>{
    return (
        <Col key={index}>
            <Food food={el}>
        </Col>
    )
})

return (
    <Container>
      <Row>
            {foodContainer}
      </Row>
    </Container>
  );

```

## <u>Bootstrap with Grid in React</u>

```js
import Container from "react-bootstrap/Container"
import Row from "react-bootstrap/Row"
import Col from "react-bootstrap/Col"
import Apod from "./components/Apod"

<Container>
    <Row>
        <h1>Space Pic des Tages</h1>
    </Row>
    <Row>
        <Apod />
    </Row>

</Container>

```

## <u>Fetch in React with then / async await</u>

```js
useEffect(()=>{
    const apiKey = "url";
    fetch(apiKey)
        .then((res)=>res.json())
        .then((json)) => {setPicture(json)}
},[])

useEffect(()=>{
    const apiKey = "url";
    const getPicture = async ()=>{
        const response = await fetch(apiKey)
        const result = await response.json()
        setPicture(result)
    }

    getPicture();

},[])

return (
    <>
        <img src={picture.hdurl}/>
        <h3>{picture.title}</h3>
        <p>{picture.explanation}</p>
    </>
)

```

## Form in React with Bootstrap
```js
import Form from "react-bootstrap/Form"
import Button from "react-bootstrap/Button"
import InputGroup from "react-bootstrap/InputGroup"
import moment from "moment"

const today = moment().format("YYYY-MM-DD")

const [date, setDate] = useState(today)
const changeHandler = (event)=>{
    setDate(event.target.value)
}

const clickHandler = ()=>{
    
}

return (
    <Form>
      <Form.Group className="mb-3" controlId="formBasicEmail">
        <Form.Label>Email address</Form.Label>
        <InputGroup>
            <Form.Control type="date" value={date} onChange={changeHandler} />
            <Button variant="outline-secondary" id="button-addon2" onClick={}>
                Button
            </Button>
        </InputGroup>
      </Form.Group>
    </Form>
)
```

## React Classes

```js
import {Component} from "react";

class App extends Components {
    constructor(props){
        super(props)

        this.state = {
            loggedIn: false
        }
    }

    logIn(){
        this.setState({
            loggedIn: !this.state.loggedIn
        })
    }

    render(){
        const {loggedIn} = this.props // deconstructing props
        return (
            <div>
                <h1>Klassenkomponenten</h1>
                <User loggedIn={this.state.loggedIn}>
                <Button onClick={this.logIn}>
                    {this.state.loggedIn ? "Ausloggen" : "Einloggen"}
                </Button>
           </div>
        )
    }
}

export default App

```

## React Classes - Lifecycles

Before mount (deprecated, wird vor dem Render ausgeführt)

    UNSAFE_componentWillMount(){}

On mount

    componentDidMount(){}

Before update (on false never update, on true always update)

    shouldComponentUpate(nextProps, nextState){
        return false
    }

On update

    componentDidUpdate(prevProps, prevState){}

Before unmount

    componentWillUnmout(){}

<h2 style="color:#37d">React Router</h2>

Installation

    npm install react-router-dom

Inside App.js
```js
import {BrowserRouter, Routes, Route} from "react-router-dom";

return (
    <BrowserRouter>
        <Routes>
            <Route path="/products" element={<Products />}>
            <Route path="/" element={<Main />}>
            <Route path="*" element={<PageNotFound />}>
        </Routes>
    </BrowserRouter>
)
```
Inside Main.js

```js
    import {Link} from "react-router-dom"

    return (
        <>
            <h1>Main</h1>
            <Link to="/products">Products</Link>
        </>
    )
```
<h2 style="color:#37d">useParams</h2>
Variables inside a Route path (inside App.js)

```js
    <Route path="/products/:id" element={<Details />}>
    <Route path="/products/:id/:name/:a/:b" element={<MoreDetails />}>
    <Route path="*" element={<Error404 />}>
```

Inside Details.js

    import {useParams} from "react-router-dom"

```js
const params = useParams();

return (
    <h1>Details {params.id}</h1>
)
```
Inside Error404.js
```js
const params = useParams();
const productExists = !!products.find(product => product.id === +params.id)

return (
    <h1>Du hast nach {params["*"]} gesucht</h1>
)
```

<h2 style="color:#37d">useNavigate</h2>

```js
import {useNavigate, useEffect} from "react-router-dom";

const navigate = useNavigate();

useEffect(()=>{
    const productExists = !!products.find(product => product.id === +params.id)

    if (!productExists){
        navigate("/404");
    }
},[params, navigate])

```
useNavigate with a component

    <Route path="/special-offer" element={<Navigate to="/products/1" />} />

```js

const ProductTest = () => {
   const productExists = !!products.find(product => product.id === +params.id)
   return productExists ? <Details /> : <Navigate to="/404" />
}

return(
    <Route path="/products/:id" element={<ProductTest />} />
)
```

<h2 style="color:#37d">useReducer</h2>

    import {useReducer} from "react";

```js

function reducer(state, action){
    switch (action.type){
        case "increment":
            return {count: state.count + 1}
        case "decrement":
            return {count: state.count - 1}
        default:
            return state
    }
}

function App(){
    const [state, dispatch] = useReducer(reducer, {count: 0})
    
    function increment(){
        dispatch({type: "increment"})
    }
    
    function decrement(){
        dispatch({type: "decrement"})
    }
    
    return (
        <button onClick={increment}>Increment</button>
        <button onClick={decrement}>Decrement</button>
    )
}

```

<h2 style="color:#37d">Context API</h2>

Inside context/Products.js

```js
import {useState, useContext} from "react";
import data from "../data";

export const ProductsContext = createContext();

function Products(props){
    const [products, setProducts] = useState(data);
    const [productsInBasket, setProductsInBasket] = useState([])
    

    return (
        <ProductsContext.Provider value={{products:products, productsInBasket: productsInBasket, setProductsInBasket, setProductsInBasket}}>
            {props.children}
        </ProductsContext.Provider>
    )
}

export default Products
```

Inside App.js

```js
import Products from "./Products"

function App(){ 

    return (
        <Products >
            <Router>
            ...
            </Router>
        </Products>
    )
}
```

Inside Home.js

```js
import {useContext} from "react";
import {ProductsContext} from "../context/Products";

function Home(){ 
    const {products} = useContext(ProductsContext)

    return (
        <div>{products}</div>
    )
}
```

<h2 style="color:#37d">Deployment</h2>

CI - continuous integration /
CD - continuous deployment

Creating a new branch

    git checkout -b <branch name>
 or

    git branch <branch name>

At github open a pull request to merge the working branch to the main branch. The supervisor has to approve and merge the branches

## Deployment with Render

[Render.com](https://render.com)

1. Static Sites < New Static Site

2. connect a repository

3. Enter data (name, root directory [empty if src], branch [], build command [$ yarn build], build [build])
   <br/><br/><br/>

# 🔵 BACKEND (BE)

### Brainstorming

- im Hintergrund (Geschäftslogik / Business Logic)
- Datenbanken (SQL / NoSQL)
- Schnittstellenn (interfaces, API)
- Datenverwaltung
- Kommunikation
- Domains
- Server

postman

Execute file in node.js

    - node <filename>
    - nodemon <filename>

## NAMING IN URL'S

<span style="color:red; font-weight:bold">Don't</span> 

    /isNumber // can lead to errors on certain systems

<span style="color:green; font-weight:bold">Do</span>

    /isnumber
    /is-number
    /is_number
  
## CREATING A SERVER WITH PLAIN JS
  
```js
import http from "http" // ES6 modules (needs additional configuration)

Inside package.json:
"type":"module"
```

```js
const http = require("http") // common js modules
```

```js
const server = http.createServer((request, response)=>{
    switch(request.url){
        case "/photos": {
            console.log("requested photos");
            response.setHeader("Content-Type", "application/json");
            response.write("my photos");
            response.end();
        }
    }
});

server.listen(4000);
```

## CREATING A SERVER WITH EXPRESS

        npm init -y
        npm i -D nodemon // install as devDependencies
        npm i express

Adjusting scripts in package.json

    "main": "server.js",
    "scripts": {
        "dev":"nodemon server.js"
        }

```js
const express = require("express");
const server = express();

server.get("/photos", (req, res) => {
    res.json("response from server")
    res.send("response from server") // send selects optimal data type
});

server.listen(4000);
```

## request.query and request.params

```js
// url: http://localhost:4000/is-number?num=1

server.get("/is_number", (req, res) => {   
    res.send(Number(req.query.num) ? "This is a number" : "This is not a number) 
});

```
```js

// url: http://localhost:4000/is_number/1914

server.get("/is_number/:num", (req, res) => {   
    Number(req.params.num) ? res.send("This is a number") : res.send("This is not a number");
});

```