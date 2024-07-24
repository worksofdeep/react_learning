
PART 5 - Password Generator



================================
PART 4: PROPS

React Fibre

tailwindcss installation

Go to framework guides 
    - copy commands related to vite/react

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

- creates tailwind.config.js:

/** @type {import('tailwindcss').Config} */
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}

- index.css
@tailwind base;
@tailwind components;
@tailwind utilities;

Props - passed as keyvalues in html tag and accessed with props


className instead of class inside jsx

function Card(props) {  // mention props if used
    console.log(props); // {}

    return (
        <>Card {props.username} </>
    )
}

OR

function Card({username = 'default', post='Not assigned'}) {  // destructing props
    console.log(props); // {}

    return (
        <>Card {username} </>
    )
}

<Card username="deep" post='SDE'
    myArr = [1,2,3] <== Error for array
    myArr = {[1,2,3]} <== correct for array
/>

let newArr = [1,2,3]; // better way to pass array
<Card myArr={newArr} />

====
PART 4: STATE:

const [counter, setCount] = useState(<initialValue>)
     <variable> <function that updates variable>

function update() {
    setCount(counter + 1)
}

- Used to update dom content with latest data




================================

emulating react with html and js

react treats everything as object

const reactElement = {
    type: 'a', // tag
    props: {
        href: "https://www.google.com",
        target: "_blank"
    },
    children: "Click to visit google"
}

const mainContainer = document.querySelector('#root')

customRender(reactElement, mainContainer) {

}

function customRender (reactElement, container) {
    const domElement = document.createElment(reactElement.type)
    domElement.innerHTML = reactElement.children
    domElement.setAttribute('href', reactElement.props.href)
    domElement.setAttribute('target', reactElement.props.target)
    container.appendChild(domElement)

    // loop render multiple
    const domElement = document.createElment(reactElement.type)
    domElement.innerHTML = reactElement.children
    for (const prop in reactElement.props) {

        if (prop === 'children') continue

        domElement.setAttribute(prop, reactElement.prop[prop])
        container.appendChild(domElement)
    }
}
===
npx create-react-app <projectname>
npm run start

npm create vite@latest
    - select React,Javascript
npm run dev
