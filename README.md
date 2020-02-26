# Compire-Necronomicon
We're using yarn as a package manager.

We’re NEVER using index as a key for a mapped component!

We're using "for of" instead of ".forEach" whenever possible. We'll replace ".map" with "for of" only when there are performance reasons for this.

We’re using function declaration for handlers, const declarations for immutable variables and let declaration for mutable variables.

We’re using “on” prefix for handlers defined in the function and “handle” prefix for handlers passed via props. onTouchStart vs props.handleTouchStart, to distinguish between own handlers and parent handlers.

We’re NEVER using HTML tags style declaration and/or nesting. no p {color: red}.

We’re using feature || fix || redesign / <task-name>-<2-3 words describing the branch> e.g. feature/MD-666-fix-Satan-called-twice
