---
title: Props
---

**What are props?**
>props (short for properties) are a Component's configuration, its options if you may. They are received from above and immutable as far as the Component receiving them is concerned. - react-guide

See : [State vs Props & Application Data](https://youtu.be/qh3dYM6Keuw?t=290) also [props vs state](https://github.com/uberVU/react-guide/blob/master/props-vs-state.md) 

**How do I pass props?**

```javascript
// manual transfer
ReactDOM.render(
  <div>
    <Shirt color="steelblue" num="3.14" size="medium"/>
  </div>,
  document.querySelector("#container")
);

```

```javascript
// using JSX spread attributes
<Component {...this.props} more="values" />
```

```javascript
// destructuring assignment with rest properties
// ensures that you pass down all the props EXCEPT the ones you're consuming yourself
function FancyCheckbox(props) {
  var { checked, ...other } = props;
  var fancyClass = checked ? 'FancyChecked' : 'FancyUnchecked';
  // `other` contains { onClick: console.log } but not the checked property
  return (
    <div {...other} className={fancyClass} />
  );
}
ReactDOM.render(
  <FancyCheckbox checked={true} onClick={console.log.bind(console)}>
    Hello world!
  </FancyCheckbox>,
  document.getElementById('example')
);
```

**How do I pass boolean values?**

* [JSX `<Foo bar={true} />` and `<Foo bar>` are equivalent](https://twitter.com/Jack_Franklin/status/768735664485568512) Jack Franklin @Jack_Franklin

**Should I use import, props, or context in React?**

* [Differences between require() and passing an object via prop or context](http://stackoverflow.com/questions/39111775/differences-between-require-and-passing-an-object-via-prop-or-context/39111942) Dan Abramov @dan_abramov

## PropTypes

> **Note:** 📌 As of React v15.5.0 prop types are separate package https://github.com/reactjs/prop-types#installation + https://facebook.github.io/react/blog/2017/04/07/react-v15.5.0.html

<hr>

>PropTypes are essentially a dictionary where you define what props your component needs and what type(s) they should be. -  Niels Gerritsen


**What are PropTypes?**
* [What are PropTypes?](https://themeteorchef.com/snippets/what-are-proptypes) Ryan Glover @themeteorchef

**Why are React PropTypes important?**
* [Why React PropTypes are important](http://wecodetheweb.com/2015/06/02/why-react-proptypes-are-important)  Niels Gerritsen @NielsG89

**How do I validate props?**
* [Better Prop Validation in React](https://medium.com/@MoeSattler/better-prop-validation-in-react-cc83590d311f#.wdhbsrlgj) Moe Sattler @travelperk

## Destructuring Props and DefaultProps
```
function ExpandableForm({ onExpand, expanded = false, children }) {
  return (
    <form style={ expanded ? { height: 'auto' } : { height: 0 } }>
      {children}
      <button onClick={onExpand}>Expand</button>
    </form>
  )
}
```

More info: [Our Best Practices for Writing React Components](https://medium.com/code-life/our-best-practices-for-writing-react-components-dec3eb5c3fc8?imm_mid=0ed2ce&cmp=em-web-na-na-newsltr_20170208#.69iorc683)
