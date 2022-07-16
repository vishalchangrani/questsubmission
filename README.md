# questsubmission

## Chapter 1 Day 1


1. Explain what the Blockchain is in your own words. 
Blockchain is fundamentally a database which is distributed, open and decentralized. It stores state like any traditional database but in addition, it is distibuted which means it runs on several hundred machines, open which means any one can query the database state and finally its decentralized meaning no single entity (organization or individual) controls it but rather it is controlled collectively by the folks who run the network.


2. Explain what a Smart Contract is.
Smart contract is code which gets deployed on the blockchain by its users and which defines what data will be stored on chain and how would it managed. In a way, it is similar to a Class defintion in object oriented language. Functions within the smart contract define what can be done with the data, how can it be accessed and updated.

3. Explain the difference between a script and a transaction.
A script is read-only and can only be used to read the data from the chain. A transaction on the other can change data on the chain. A script can be executed for free against a chain while one needs to pay to execute a transaction.


## Chapter 1 Day 2

What are the 5 Cadence Programming Language Pillars?
1. Safety and security
2. Clarity
3. Approachability
4. Developer Experience
5. Resource Oriented Programming

In your opinion, even without knowing anything about the Blockchain or coding, why could the 5 Pillars be useful (you don't have to answer this for #5)?

The 5 pillars is what makes Cadence more trustworthy and in turn makes the Flow blockchain more trustworthy and reliable. If I know that the smart contract that I am deploying is secure, clearly does what I want, easily explainable, easier to write and maintain then I will feel more assured that my Dapps will work as they are supposed to work.


## Chapter 2 Day 1
![Screen Shot 2022-07-16 at 2 45 39 PM](https://user-images.githubusercontent.com/1117327/179372832-e25c5e2d-fceb-4ab7-857e-56df3f3a4ab8.png)
![Screen Shot 2022-07-16 at 10 42 44 AM](https://user-images.githubusercontent.com/1117327/179366253-93504d64-0ef8-417a-af82-bff7544cae79.png)

## Chapter 2 Day 2
1. Explain why we wouldn't call changeGreeting in a script.

A script is only meant to read data, not modify it. Hence, we wouldn't call `changeGreeting` in a script.

What does the AuthAccount mean in the prepare phase of the transaction?

`Authaccount` is the one who pays for the transaction. In the prepare phase, information from the `AuthAccount` can be accessed.

What is the difference between the prepare phase and the execute phase in the transaction?

Prepare phase is where the transaction can access data of the authorizer account. Execute phase is where the data in the account should be modified.

This is the hardest quest so far, so if it takes you some time, do not worry! I can help you in the Discord if you have questions.

Add two new things inside your contract:

A variable named myNumber that has type Int (set it to 0 when the contract is deployed)
A function named updateMyNumber that takes in a new number named newNumber as a parameter that has type Int and updates myNumber to be newNumber
Add a script that reads myNumber from the contract

Add a transaction that takes in a parameter named myNewNumber and passes it into the updateMyNumber function. Verify that your number changed by running the script again.

![Screen Shot 2022-07-16 at 11 22 58 AM](https://user-images.githubusercontent.com/1117327/179367511-99d57274-820c-456c-892d-70eefdb0f312.png)
![Screen Shot 2022-07-16 at 11 23 08 AM](https://user-images.githubusercontent.com/1117327/179367529-840c0296-6250-4a3f-bf74-2e9d89b64675.png)
![Screen Shot 2022-07-16 at 11 22 50 AM](https://user-images.githubusercontent.com/1117327/179367547-ce7b6c14-9a1d-421a-93de-b01d433b7d52.png)

