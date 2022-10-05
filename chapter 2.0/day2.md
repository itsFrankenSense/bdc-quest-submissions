## Quests

**1. Change the color of "Emerald DApp" to whatever color you want**
<br>
**2. Change the font size of the title**
<br>

``` HTML
.main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.title {
  font-size: 25px;
}

.title a {
  color: #f00;
  text-decoration: none;
}
````
<br>

**3. Change the "Emerald DApp" link to a different link (this means messing with the < a > tag)**
<br>
**4. There are two parts.
 <br> i. Inside of your < main > tag, add a < p > tag and put whatever text you want in it.**
<br>

``` HTML
import Head from 'next/head'
import styles from '../styles/Home.module.css'

export default function Home() {
  return (
    <div className={styles.container}>
      <Head>
        <title>Emerald DApp</title>
        <meta name="description" content="Created by Emerald Academy" />
        <link rel="icon" href="https://i.imgur.com/hvNtbgD.png" />
      </Head>

      <main className={styles.main}>
        <p>Whatever text you want</p>
        <h1 className={styles.title}>
          Welcome to my <a href="https://twitter.com/itsfrankensense" target="_blank">Emerald DApp!</a>
        </h1>
      </main>
    </div>
  )
}
```
  
**ii. Go to the .main class and add this line: flex-direction: column. Watch what it does!**
<br> - Created the text in a column view.

![image](https://user-images.githubusercontent.com/111278229/193976549-a36954b6-6b50-4aca-9327-0c7fc25af97c.png)

