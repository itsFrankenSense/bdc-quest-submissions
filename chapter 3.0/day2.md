## Quests

**1. Explain why we wouldn't call changeGreeting in a script.**
<br> - A script can not modify data. Transactions must be used to change information on the blockchain.

**2. What does the AuthAccount mean in the prepare phase of the transaction?**
<br> - AuthAccount is used to provide access to the users storage.

**3. What is the difference between the prepare phase and the execute phase in the transaction?**
<br> - Prepare can complete anything that can be done in execute as well. The two sections are split to provide clearer coding.
<br> In the prepare phase you can also pass in things like the signer or account being used.

**4.Add two new things inside your contract:**
<br>
i. A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
<br> ii. A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
<br> iii. Add a script that reads myNumber from the contract

iv. Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

<br>
<br> - Contract

![image](https://user-images.githubusercontent.com/111278229/194690158-da9a65c0-5852-4aa4-b40e-01f613777718.png)


<br> - Transaction

![image](https://user-images.githubusercontent.com/111278229/194690162-ed680954-19aa-4ab5-8cc7-beeab4f0c3c9.png)


<br> - Script

![image](https://user-images.githubusercontent.com/111278229/194690165-387a2b16-c199-4c1b-8a48-57374b73e7a3.png)
