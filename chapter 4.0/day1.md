## Quests

**1. How did we get the address of the user? Please explain in words and then in code.**
<br> - We added a javascript line `user.loggedIn ? user.addr : "Log In"` inside the HTML for our button. This displays user.addr (their address stored in the user variable) if they are logged in or 'Log In' if they are not logged in. 
<br> - ```<button onClick={handleAuthentication}>{user.loggedIn ? user.addr : "Log In"}</button>``` this is the code to display the users address.

**2. What do fcl.authenticate and fcl.unauthenticate do?**
<br> - This is used to handle the user logged-in and logged-out state. Used in our DApp with the log-in button onClick 'handleAuthentication'.

**3. Why did we make a config.js file? What does it do?**
<br> - This allows us to connect to Flow TestNet, and load our wallets (from FCL Directory) 

**4. What does our useEffect do?**
<br> - `useEffect` runs whatever is set inside the `{}` when the page is refreshed. In our case the brackets are empty, and the code above is ran.
``` html
useEffect(() => {
    fcl.currentUser.subscribe(setUser);
  }, [])
```
**5. How do we import FCL?**
<br> - inside `./components/Nav.jsx` we add `import * as fcl from "@onflow/fcl";`

**6. What does fcl.currentUser.subscribe(setUser); do?**
<br> - For our DApp we retain the 'user' variable even if the page is refreshed. An example of this is that the end-user doesn't have to log-in everytime the page is refreshed, and their wallet address is still retained on the log-in button.
