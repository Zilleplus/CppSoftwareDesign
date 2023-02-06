# Guideline 1: Understand the Importance of Software Design
## The problem of dependencies

- Unavoidable dependencies: part of the original problem.
- Aritificial dependencies: should be avoided.

## Three Levels of software design

1. Software Architecture: Client server architecture, Microservices, ...
2. Software Design: maintainability, testability, scalability, Strategy pattern, Visitor Pattern, ...
3. Implementation Details: What C++ standard, implementation pattern, factory function, ...

## The focus on features
- Language features will not save a project, they mearly improve ergnomics.
- It's usefull to talk about how certain features can be used to implement patterns/design's/architectures.

## The focus on software design and design principles
- Most focused on subject of the book. (hence the title of the book)

## Summary
- Treat software design as an essentials part of writing software.
- Focus less on C++ language detrails and more on software design.
- Make sofware adaptable to frequent changes
- Avoid unnecesaary coupling and dependencies to make software more changeable.
- Understand software design as the art of managing dependencies and abstractions.
- Consider the boundary between software design and software architecture as fluent.

# Guideline 2: Design for change
## separation of concerns
- Easy way to reduce aritificial dependencies.
- "Orthogonality"
- "Single responsiblity"

## example
- class with virtual member methods on that execute complex logic.
- The author argues this is bad, as a change to that kind of logic will require you to change stuff all over the codebase. (I agree completely with this)

## Logical vs Physical coupling
- Dependencies of dependencies end up affecting the least generic classes
-> By seperating off the logic in seperate class -> This does not happen -> how we seperate it off is discussed furth on in the book.

## Don't repeat yourself

## Avoid premature separation of concerns
- YAGNI -> You aren't gonna need it

## Summary
- Expect change in software.
- Desgin for easy change.
- Avoid combining unrelated changes, Orthogonal aspecs in the same class to prevent coupling.
- Understand that coupling increases the likeihood for change and makes changes harder.
- Adhere to the Single-Reponsibility principle (SRP) to seperate concerns.
- Follow the DRY principle
- Avoid premature abstraction if you are not sure about the next change

# Guideline 3: Separate interfaces to avoid aritificial coupling
- SOLID: The I stands for "Interface Segregation Principle" (ISP), "Clients should not be forced to depend on methods that they do not use.".
- ISP is a special case of SRP (Seperation of concerns)

example:

```
template<std::forward_iterator ForwardIt, std::forward_iterator OutputIt>
OutputIt copy(ForwardIt first, ForwardIt last, ForwardIt d_first)
```

If we use forward\_iterator as a constraint on std::copy, we won't be able to use it with iterators that can only do one pass. If we use InputIterator it will still work with forward\_iterators but also with single pass iterators(aka InputIterators).

## Summary
- Remember that coupling also affects interfaces.
- Adhere to the Interface Segregation Principle to seperate concerns in interfaces (ISP).
- Consider theISP as a special case of the Single-Reponsibility Principle (SRP).
- Understand that ISP helps for both inheritance hierarchies and templates.

# Guideline 4: Design for testability
- Tests avoid regression bugs, when making changes.
- Free your functions. (Scott Meyers)

## Summary
- Understand that tests are your portection layers against accidentally breaking things.
- Remember that tests are essential, and so is testability.
- Seperate concerns for the sake of testibility.
- Consider private member-functoins that need testing to be misplaced.
- Prefer non-member non-friend functions to member functions.

# Guideline 5: Design for extension
- Open-Closed Principle
"Software artifacs should be open for extension, but closed for modification." Bertrand Meyer

## Summary
- Design for easy extension.
- Adhere to the Open-Closed Principle to keep code open for extension, but closed for midification.
- Avoid premature abstractions if you are not sure about the next addition.
