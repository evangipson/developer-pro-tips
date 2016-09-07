# Developer Pro-tips
A collection of rules to ensure success in your development career, licensed under <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.
- Understand the full scope
  - If you are making a code change, you need to understand the full scope of that change (the full method, whatever the scope is).
- Look up your project's and language's conventions
  - Look up the naming conventions of the project you're working on and follow them. If there are none look up the language conventions.
  - e.g. C# suggests private stuff gets camelCase and public stuff (things you can see outside of an object) gets PascalCase 
- DRY: don't repeat yourself
  - don't duplicate code and if you must then comment clearly that you are doing so in both places.
- Automate repetitive tasks
  - Before doing something twice, think about if you have to do it a 3rd time (or more.) if so, automate it!
- Null check
  - Protect yourself against data you get from outside your program (like database calls, API calls) with a null check.
  - Always think about where your data is coming from and what happens if you don't get that data.
- Protect your users from evil
  - Doubly protect yourself against data that comes in to your server from users. Always think about what happens if the user is malicious. Be familiar with the [top 10 threats from OWASP](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet).
- Existing code is not holy
  - Just because something is done that way doesn't make a case to do it that way.
  - That said, follow convention if there's no good reason to break it
  - If an existing convention is bad then form a plan to gradually improve it and discuss with your team.
- You are not your code
  - Code may feel like art when you are writing it, but it's a machine built to work. Solicit improvements from peers.
- Your code is your teams' code
  - And vice versa
- Use source control well
  - Look up its conventions too. Here are [10 commandments of good source control management](https://www.troyhunt.com/10-commandments-of-good-source-control/)
- It's harder to read code than to write it
  - Assume the next person to read your code is not you and that you have a sudden onset of amnesia.
- Separate your concerns
  - Write display logic in CSS, write behavior logic in JavaScript, write out DOM structure in HTML.
  - You don't want to call in a JavaScript guy to change an image color, and you don't want to call a CSS guy to add and remove a class from an element conditionally.
  

