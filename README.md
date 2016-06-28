# Developer Pro-tips
A collection of rules to ensure success in your development career.

# Coding Tips
- If you are making a code change, you need to understand the full scope of that change (the full method, whatever the scope is).
- private stuff gets camelCase, public stuff (things you can see outside of scope) gets PascalCase
- DRY means don't repeat yourself - don't duplicate code and if you must then comment clearly that you are doing so in both places.
- Before doing something twice, think about if you have to do it a 3rd time (or more.) if so, automate it!
- Protect yourself against third party data (like database calls, API calls) with a null check. Always think about where your data is coming from and what happens if you don't get that data.
- Existing code is not holy
  - Just because something is done that way doesn't make a case to do it that way.
