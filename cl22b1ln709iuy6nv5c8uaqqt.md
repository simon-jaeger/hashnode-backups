## A love letter to React function components

These days, we have an abundance of JavaScript frameworks to choose from. I've had my fair share of experience with a few of them, from Angular to Vue and even some Svelte and Alpine. But one Framework that stands out from the rest to me, is React. Why is that? Where other frameworks create dozens of abstractions and APIs, React seemingly almost vanishes from you code by sticking very close to how JavaScript actually works. Let me explain with an example.

Please take a minute to think about how you'd build a simple component system with vanilla JavaScript, no framework, no nothing. Got it? Chances are, you're thinking about a simple function that takes in some parameters and returns some HTML. Something kind of like this:

```ts
// component
function Card(props: { title: string, body: string }) {
  return `<div>
    <h2>${props.title}</h2>
    <p>${props.body}</p>
  </div>`
}

// usage
document.body.innerHTML = `
  <h1>Welcome to my website</h1>
  ${Card({
    title: "HTML",
    body: "Defines the meaning and structure of web content",
  })}
  
  ${Card({
    title: "CSS",
    body: "Describes the presentation of a document written in HTML",
  })}
`
```

I've taken the liberty to use TypeScript to make it a bit more robust and self-documenting, but that's optional. As you can see, we're just defining a simple reusable function and call it inside our page template later to create instances of our component. Intuitive, simple and without any vendor specific boilerplate.

Please proceed to take a look at the following React code:

```ts
// component
function Card(props: { title: string, body: string }) {
  return <div>
    <h2>{props.title}</h2>
    <p>{props.body}</p>
  </div>
}

// usage
function App() {
  return <div>
    <h1>Welcome to my website</h1>
    <Card
      title="HTML"
      body="Defines the meaning and structure of web content"
    />
    <Card
      title="CSS"
      body="Describes the presentation of a document written in HTML"
    />
  </div>
}
```

Looks familiar, wouldn't you agree? All I had to do is remove the backticks around the HTML and the `$` before the variable interpolation to turn the template string into what's known as JSX. And instead of calling the function directly, we can now call it with a syntax closer to normal HTML, where the tag name is the function name and the arguments are passed like attributes. Under the hood, it's still a good old function though. And that's the beauty of it.

Instead of introducing its own way of defining properties, like Angular or Vue do, React embraces JavaScript's native capabilities. Components are simply functions, properties simply arguments. This also means that we can do everything with them we can do with ordinary functions, like making the arguments type safe with TypeScript, again, without adding any kind of framework specific boilerplate.

This philosophy is why I have such high hopes for the future of React. By keeping its API light, almost invisible, the maintenance horror of future API changes reduces drastically. It's also easier to get started, because, in the end, it's just JavaScript the way you know and love it. JSX might look scary at first, especially if you aren't used to functions like `map()` or short-circuit evaluation, but I urge you to give it a try, even if you may have disliked it at first glance.

In my opinion, more frameworks should strive to reduce – and not increase – their surface area the way React did with its function components. Elegance lies in simplicity after all, right?
