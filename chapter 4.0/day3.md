## Quests

Write a function that executes a script with all the Cadence types that we reviewed today. Call the script when the page refreshes. Return something random from the Cadence script, and console log it to prove to me your script actually worked.

![image](https://user-images.githubusercontent.com/111278229/195724897-eff4635e-95ac-45b8-8126-887214e69898.png)


``` javascript
import { useState, useEffect } from 'react'
import Head from 'next/head'
import styles from '../styles/Home.module.css'
import Nav from "../components/Nav.jsx"
import * as fcl from "@onflow/fcl"

export default function Home() {
  const [greeting, setGreeting] = useState('');
  const [newGreeting, setNewGreeting] = useState('');
  function runTransaction() {
    console.log(newGreeting)
  }

  async function runSimpleTypes() {
    const simpleTypes = await fcl.query({
      cadence: `
      pub fun main(
        a: Int, 
        b: String, 
        c: UFix64, 
        d: Address, 
        e: Bool,
        f: String?,
        g: [Int],
        h: {String: Address}
      ): [Int] {
        return g
      }
      `,
      args: (arg, t) => [
        arg("29", t.Int),
        arg("BZ is the BEEZ", t.String),
        arg("29.0", t.UFix64),
        arg("0x1ab2c3d456789e0f", t.Address),
        arg(false, t.Bool),
        arg(null, t.Optional(t.String)),
        arg([29, 50, 23], t.Array(t.Int)),
        arg(
          [
            { key: "Blocto", value: "0x68c06ab43446d8f1" },
            { key: "Dapper", value: "0x7a3a0ecac1a861e2" }
          ], 
          t.Dictionary({ key: t.String, value: t.Address })
        )
      ]
    });
  
    console.log(simpleTypes)
  }
  useEffect(() => {
    runSimpleTypes()
  }, [])

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
      </main>
    </div>
  )
}
```
