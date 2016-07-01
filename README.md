# Developer Pro-tips
A collection of rules to ensure success in your development career.

# Coding Tips
- Understand the full scope
  - If you are making a code change, you need to understand the full scope of that change (the full method, whatever the scope is).
- Look up your project and language conventions
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
