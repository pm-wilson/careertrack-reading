## Quantity Always Trumps Quality

1. What the title means is that quantity helps create the quality. Practice makes perfect can sum it up pretty well too.
2. The best way to make good quality code (or anything else) is to practice more, and worry about being perfect less. As you gain experience the perfection will come.
3. The author puts it this way

- Stop theorizing
- Write lots of software
- Learn from your mistakes

4. We need to build software in order to learn it, so keep building until it is where you want it.

## Clean Code

1. The only valid measurement of code quality is WTF's per minute.
2. Wading through code is when you write bad code that is difficult to maintain.
3. On an organization level, as messy code grows management can only add people and pressure them to increase productivity, which causes more problems if they do not understand the code base they are working on. As time increases, productivity approaches 0.
4. Writing messy code to make a deadline will only make the next deadline worse.
5. Clean code should be easy for other developers to read and maintain. To do this, everything should do just one thing.

## Red, Gree, Refactor

1. Red: think about what you want to develop, and get down the basic information on the screen, at this point the test should not be passing.
2. Green: think about how to make the tests pass, at this point you should be finding a solution by any means possible and not worrying about how wet, or hard to understand it might be.
3. Refactor: think about how to improve your existing implementation, think about how the code could be faster or easier to understand.

## Cycles of TDD

1. TDD Testing started off as a line by line, write a test just so it doesn't pass, and write code just enough to make the test pass, back and fourth. This is the second by second style.
2. The minute by minute style is red, green, refactor and is about creating a test that fails, make it pass, and clean up the mess.
3. The 10 minute style is about when production code gets more general and the behavior gets more specific. This is similar to the previous style, but gets checked to be sure we are on track to meet big picture goals.
4. The hour by hour style is stopping each hour to see what the direction the code should go and what constraints will define those.
