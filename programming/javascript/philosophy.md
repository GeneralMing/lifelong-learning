# Practical Ways to Write Better JavaScript
[Reference](https://stackoverflow.blog/2019/09/12/practical-ways-to-write-better-javascript/)

- TS: This makes refactoring larger applications possible.
  - *Most of the pain of refactoring JS is due to the fact that it doesn't enforce function signatures.*
  - When TS is setup correctly, it will be difficult to write code without first defining your interface and classes. This provides a way to share concise, communicative architecture proposals.
  - I believe forcing developers to define interfaces and APIs first results in better code.
- Use modern features:
  - `async` and `await`: this is functionally equivalent to `Promise`.
  - `let` and `const` and `arrow` or anonymous functions.
  - Spread operator, template literals/interpolating, object destructuring.

```
function animalParty({ dog, cat }) {} // Can destructure in method signature

const myDict = {
  dog: 'woof',
  cat: 'meow',
};
```

- Assume your system is distributed.
  - JS is single threaded, but not single-file. Even though it isn't parallel, it's still concurrent.
  - JS solves HTTP blockage with the event loop. The event loop loops through registered events and executes them based on internal scheduling/prioritisation logic.
  - JS for loops should only be used if absolutely necessary. Otherwise, use `map`, `map` with index, `for-each`.
  - Map can be run concurrently.
- Lint your code and enforce a style. As they are opinionated, take it with a grain of salt.
- Test your code:
  - Test driver: Jest, Mocha, Jasmine, Ava.
  - Spies and stubs: Sinon.
  - Mocks: Nock.
  - Web automation: Selenium, Cypress, PhantomJS.

# # Inside Linear's Engineering Culture

- I started developing on iOS back in 2008, when the iPhone came out. I built an RSS reader early on, and it made quite a bit of money because it was one of the first apps of its type in the App Store. From then, I was hooked and created a bunch of apps on the side. I built iOS apps, as my main jobs were more backend-related. In China, I built a sync engine, and at Groupon I started out on the backend, but after merging with the Point-of-Sale team I worked on iOS full time. When I interviewed at Uber and I wanted to work on customer facing mobile, but quickly after joining the mobile platform team was formed and I was asked to manage the team. Later I moved back to being an individual contributor (IC) working as a senior staff engineer.
- For me, working in Silicon Valley was the best schooling I could get as a software engineer. It was not until later that I appreciated the significance of the pedigree which comes from working at high-profile tech companies.
- **As a founder, if you want getting investment to be relatively easy, work at a big company first**. After that, you're on the radar of investors. And if you have a founding team with Big Tech pedigree, the idea you’re pitching becomes less important as a selling point. In our case, our founding team came from Airbnb, Coinbase and Uber.

## The Idea of Linear

- While we knew we could build a better project management solution for ICs, we were not excited by the thought of building _yet another_ project management software.
- Most teams used bits and pieces from Scrum and couldn’t really explain why they were working in sprints.