## Quests

**1. Change the printHello function to be called runTransaction.**
<br>
**2. Change the "Hello" text inside the button to "Run Transaction".**
<br>
**3. Inside the runTransaction function, add some code to console log your newGreeting variable to the developer console.**
<br>
**4. Go back to your webpage, type something into the input box, and press "Run Transaction". Open your developer console and you will see some thing being printed!**
<br>
**To upload your quests, show us your ./pages/index.js file and take a screenshot of your newGreeting being printed to the developer console.**
<br>

``` HTML
import { useState } from 'react';

import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from "../components/Nav.jsx"

export default function Home() {
  const [newGreeting, setNewGreeting] = useState('');
  function runTransaction() {
    console.log(newGreeting)
  }
  function printGoodbye() {
    console.log("Goodbye.")
  }
  return (
    <div className={styles.container}>
      <Head>
        <title>Emerald DApp</title>
        <meta name="description" content="Created by Emerald Academy" />
        <link rel="icon" href="https://i.imgur.com/hvNtbgD.png" />
      </Head>

      <Nav />

      <main className={styles.main}>
      <h1 className={styles.title}>
    Welcome to my <a href="https://academy.ecdao.org" target="_blank">Emerald DApp!</a>
  </h1>
  <p>This is a DApp created by FrankenSense.</p>

<div className={styles.flex}>
    <button onClick={runTransaction}>Run Transaction</button> 
    <input onChange={(e) => setNewGreeting(e.target.value)} placeholder="Hello, Idiots!" />
</div>
  
</main>
    </div>
  )

}
```

![image](https://user-images.githubusercontent.com/111278229/194445242-c61fc890-ce4d-4342-91b3-8dedbb1bc3b6.png)

