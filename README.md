# Compire-Necronomicon
1. We're using yarn as a package manager.

2. We’re NEVER using index as a key for a mapped component!
```
const array = [{id: 1}, {id:2}];

//Don't
const renderedItems = array.map((item, idx) => <Item key={idx}/>);

//Do
const renderedItems = array.map(item => <Item key={item.id}/>);
```

3. We're using "for of" instead of ".forEach" whenever possible. We'll replace ".map" with "for of" only when there are performance reasons for this.
```
const array = [1, 2, 3];

//Don't 
array.forEach(item => console.log(item))

//Do
for (const item of array) {
  console.log(item);
}
```

4. We’re using function declaration for handlers, const declarations for immutable variables and let declaration for mutable variables.
```
//handler
function onClick(e) {
  e.preventDefault();
}

// immutable
const isLoggedIn = userInfo != null;

//mutated later
let buttonText = 'sign in';

if (loggedIn) {
  buttonText = 'sign out';
}
```

5. We’re using “on” prefix for handlers defined in the function and “handle” prefix for handlers passed via props. onTouchStart vs props.handleTouchStart, to distinguish between own handlers and parent handlers.

```
function onClick(e) {
  props.handleClick();
}

<div onClick={onClick}/>

//destructured before, instantly known to be from parent
<div onClick={handleClick}/>
```

6. We’re NEVER using HTML tags style declaration and/or nesting.
```


.item {
//NO!
  p {
  color: red
  }
}
```

7. We’re using a system for branch naming: [feature || fix || redesign]/[task number]-[2-3 words describing the branch] e.g. feature/MD-666-fix-Satan-called-twice
