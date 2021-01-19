# Compire-Necronomicon
1. We're using yarn as a package manager.

2. We try to avoid using index as a key for a mapped component!
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

4. We’re using, const declarations for immutable variables and functions and let declaration for mutable variables.
```
//handler
const onClick = e => {
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

5. We’re using “handle” prefix for handlers defined in the function and “on” prefix for handlers passed via props. handleTouchStart vs props.onTouchStart, to distinguish between own handlers and parent handlers.

```
function handleClick(e) {
  props.onClickClick();
}

<div onClick={handleClick}/>

//destructured before, instantly known to be from parent
<div onClick={onClick}/>
```

6. We’re using a system for branch naming: [feature || fix || redesign]/[task number]-[2-3 words describing the branch] e.g. feature/MD-666-fix-Satan-called-twice

7. We're using functional components for almost all new components, no classes, except when strictly necessary for performance reasons (keeping method references equal during rerenders).

8. We use useSelector and useDispatch hooks to connect to redux store via react-redux. No mapStateToProps in functional components.

9. We use reselect for memoizing complex state variables and composing those into optimized selectors that don't rerender the whole tree when the values don't change. This package needs to be added only when there is a performance bottleneck, either existing or expected.

110 We import lodash specific functions instead of the whole library for the tree shaking to take effect.
```
//DON'T
import _ from 'lodash';
//this also doesn't shake that tree, unfortunately. You can find more info on webpack website about tree shaking.
import {cloneDeep, isEmpty} from 'lodash';

//DO
import cloneDeep from 'lodash/cloneDeep';
import isEmpty from 'lodash/isEmpty';
import last from 'lodash/last';
import uniqBy from 'lodash/uniqBy';
import get from 'lodash/get';
```

11. We use != / == null verifications for all variables, and !<variable> for booleans only.

```
//DON'T

const user = userSelector(state);
if (!user){
//do something
  if (!refetchAttempted){
    //refetch
    }
} 

//DO 
const user = userSelector(state);
if (user == null){
//do something
  if (!refetchAttempted){
    //refetch
    }
} 
```
