---
title: React Hooks - useContext()
date: 2019-10-20T12:51:00.000Z
---

Avoid prop drilling with React's Context API

<!-- more -->

## There Will Be Props

Context in react is a way for components to access application state without needing pass props down through components.

I had already built a few application with React before I heard the term "Prop Drilling" and because at that point I had not yet learned Redux (another state management solution) I needed no further explanation.

![Still from film 'There Will Be Blood'. Oil rig on fire](https://res.cloudinary.com/dscjol9s7/image/upload/v1578264270/1_iV9lDoH8Zsu21bxRURps1Q_ffg0ft.jpg)

Component composition in Javascript frameworks and design systems helps us break code up into smaller, bite sized, self-contained bits which is super helpful in creating readable, maintainable code.

As applications become more complex, components often need to access state that is located further away on the rendering tree. The solution would be to move the shared state to the nearest ancestor of both components and just "drill" state as a prop down through the component tree until you get to the component that needs it.

This means that a relatively minor change could require you to touch several files to alter components which is time consuming, annoying, and increases the chances for bugs.

With context we can declare that a piece of state will need to be accessed elsewhere and not as prop values from the parent component. This is especially helpful for application state that will be used globally and accessible to all components.

## React's Context API

This example demonstrates how we can use context to toggle between to user states.

Here's our user data :

```jsx
//User Data
const monsters = {
  freddy: {
    name: "Freddy Kruger",
    movie: "nightmare on elm street",
    specialSkills: [
      "Sharp nails",
      "Haunts dreams",
      "Can pull off horizontal stripes"
    ]
  },
  jason: {
    name: "Jason Voorhees",
    movie: "friday the 13th",
    specialSkills: [
      "Cannot die",
      "Machete skills",
      "Punishing irresponsible camp counselors"
    ]
  }
};
```

First we need to declare a variable to hold the React.createContext method and pass it some initial values.

```jsx
const MonsterContext = React.createContext({
  monster: {},
  toggleMonster: () => {}
});
```

Then we wrap our App component with the context provider.

```jsx
function App() {
  const [current, toggleCurrent] = useState(monsters.freddy);
  return (
    <div className="App">
      <MonsterContext.Provider
        value={{
          monster: current,
          toggleMonster: () =>
            toggleCurrent(
              current === monsters.jason ? monsters.freddy : monsters.jason
            )
        }}
      >
        <Profile />
      </MonsterContext.Provider>
    </div>
  );
}
```

Note that our App component will need to track the state of the user so using the useState.

Next we make our profile component which has a heading as well as user specific detail which we will define in our CurrentMonster.

```jsx
function Profile() {
  return (
    <div>
      <h1>Monster Dates</h1>
      <CurrentMonster />
      <NewMonsterBtn />
    </div>
  );
}
```

In our CurrentMonster we need to access our context data using the useContext functon and passing in our MonsterContext

```jsx
function CurrentMonster() {
  const { monster } = useContext(MonsterContext);

  return (
    <section>
      <h2>{monster.name}</h2>
      <h3>Special SKills:</h3>
      <ul>
        {monster.specialSkills.map((skill, indx) => {
          return <li key={indx}>{skill}</li>;
        })}
      </ul>
    </section>
  );
}
```

We also want to make a component so we can update our context state.

```jsx
function NewMonsterBtn() {
  const { toggleMonster } = useContext(MonsterContext);
  return <button onClick={toggleMonster}> Monster </button>;
}
```

You can check out the [Code Sandbox](https://codesandbox.io/s/usecontext-example-hs0sh) if you want to explore and play around with the code

Here's the full javascript code.

```jsx
const monsters = {
  freddy: {
    name: "Freddy Kruger",
    movie: "nightmare on elm street",
    avatar:
      "https://i.pinimg.com/originals/b1/07/a7/b107a7d0367835bc3375ce41b6a6d64e.jpg",
    specialSkills: [
      "Sharp nails",
      "Haunts dreams",
      "Can pull off horizontal stripes"
    ]
  },
  jason: {
    name: "Jason Voorhees",
    movie: "friday the 13th",
    avatar:
      "https://res.cloudinary.com/teepublic/image/private/s--LgVynWYp--/t_Preview/b_rgb:191919,c_limit,f_jpg,h_630,q_90,w_630/v1475591344/production/designs/713330_1.jpg",
    specialSkills: [
      "Cannot die",
      "Machete skills",
      "Punishing irresponsible camp counselors"
    ]
  }
};

const MonsterContext = React.createContext({
  monster: monsters.jason,
  toggleMonster: () => monsters.freddy
});

function App() {
  const [current, toggleCurrent] = useState(monsters.freddy);
  return (
    <div className="App">
      <FaceOff>
        <MonsterContext.Provider
          value={{
            monster: current,
            toggleMonster: () =>
              toggleCurrent(
                current === monsters.jason ? monsters.freddy : monsters.jason
              )
          }}>
          <Profile />
        </MonsterContext.Provider>
      </FaceOff>
    </div>
  );
}

function Profile() {
  return (
    <div className="profile-container">
      <div className="img-container">
        <img
          src="https://res.cloudinary.com/dscjol9s7/image/upload/v1571778112/freddie-vs-jason_fan-art_a3texh.jpg"
          alt=""
        />
      </div>
      <h1>Monster Stats</h1>
      <CurrentMonster />
      <NewMonsterBtn />
    </div>
  );
}

function NewMonsterBtn() {
  const { toggleMonster, monster } = useContext(MonsterContext);
  return (
    <button onClick={toggleMonster}>
      {monster.name === "Freddy Kruger" ? "View Jason" : "View Freddy"}{" "}
    </button>
  );
}

function CurrentMonster() {
  const { monster } = useContext(MonsterContext);

  return (
    <section>
      <h2>{monster.name}</h2>
      <div className="avatar-container">
        <img src={monster.avatar} alt={avatar of ${monster.name}`} />
      </div>
      <h3>Special Skills:</h3>
      <ul>
        {monster.specialSkills.map((skill, indx) => {
          return <li key={indx}>{skill}</li>;
        })}
      </ul>
    </section>
  );
}
```
