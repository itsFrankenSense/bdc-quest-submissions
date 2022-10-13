## Quests

**1. Instead of console logging the result after the script executes, I want you to:**
<br>i. Make a new variable named greeting using useState
<br>ii. Set the greeting variable to the response of the script call
<br>iii. Create a `<p>` tag after the `<div className={styles.flex}>` tag
<br>iv. Put the greeting variable inside of that `<p>` tag. This will make the result of your script show on your webpage!

**2. I deployed a contract called SimpleTest to an account with an address of 0x6c0d53c676256e8c.** 
I want you to make a button that, when clicked, executes a script to read the number variable from that contract. 
If you're curious, you can see the contract here: https://flow-view-source.com/testnet/account/0x6c0d53c676256e8c/contract/SimpleTest

Submit all the code you used to call the script, and the result of the script.

``` javascript
import { useState, useEffect } from 'react'
import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from "../components/Nav.jsx"
import * as fcl from "@onflow/fcl"

export default function Home() {
  const [greeting, setGreeting] = useState('');
  const [newGreeting, setNewGreeting] = useState('');
  const [number, setNumber] = useState ('');
  function runTransaction() {
    console.log(newGreeting)
  }

  async function runSimpleNumber() {
    const simpleNumber = await fcl.query({
      cadence: `
      import SimpleTest from 0x6c0d53c676256e8c

      pub fun main(): Int {
      return SimpleTest.number
      }   
      `,
      args: (arg, t) => [] // ARGUMENTS GO IN HERE
    });
  
    setNumber(simpleNumber)
  }

  async function executeScript() {
    const response = await fcl.query({
      cadence: `
      import HelloWorld from 0x2d7a5f7643681c7a
  
      pub fun main(): String {
          return HelloWorld.greeting
      }
      `, 
      args: (arg, t) => [] // ARGUMENTS GO IN HERE
    })
  
    setGreeting(response)
  }

  useEffect(() => {
    executeScript()
  }, [])

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

        <p>{greeting}</p> 

        <button onClick={runSimpleNumber}>Find Number</button> 
        <p>Your Number is: {number}</p>
      </main>
    </div>
  )
}
```

<br>

![image](https://user-images.githubusercontent.com/111278229/195716476-3113dd15-a7a7-4f0f-a73f-275518be9574.png)


**3. Then, I want you to remove the button, and make the script execute every time the page refreshes.**

Submit all the code you used to do this.
``` javascript
  async function runSimpleNumber() {
    const simpleNumber = await fcl.query({
      cadence: `
      import SimpleTest from 0x6c0d53c676256e8c

      pub fun main(): Int {
      return SimpleTest.number
      }   
      `,
      args: (arg, t) => [] // ARGUMENTS GO IN HERE
    });
  
    setNumber(simpleNumber)
  }
  useEffect(() => {
    runSimpleNumber()
  }, [])
```
