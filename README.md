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
![Screen Shot 2022-07-16 at 2 51 32 PM](https://user-images.githubusercontent.com/1117327/179372949-f62f5de0-4e3c-4f86-86af-994ea6059434.png)
![Screen Shot 2022-07-16 at 2 51 22 PM](https://user-images.githubusercontent.com/1117327/179372951-bd14fb4b-2cfe-4ef3-ad8f-dee1bb2ba102.png)
![Screen Shot 2022-07-16 at 2 51 16 PM](https://user-images.githubusercontent.com/1117327/179372954-6f55d1e2-aca2-4d02-8134-94d0ebd312d1.png)


## Chapter 2 Day 3
![Screen Shot 2022-07-16 at 4 04 30 PM](https://user-images.githubusercontent.com/1117327/179374524-455f4d7d-b0c6-4ab9-a68b-1422d6e91228.png)

Quest 4
Using this picture below, explain...
What the error message means

The error indicates that an optional is being returned while the method signature defines a non-optional String type.

Why we're getting this error

A value from a dictionary is returned as optional and hence the return type for the function needs to be made optional.

How to fix it

Changing the function signature to
`pub fun main(): String? {` should fix the error

## Chapter 2 Day 4

![Screen Shot 2022-07-17 at 10 03 59 PM](https://user-images.githubusercontent.com/1117327/179448298-14be193f-edb1-4e92-8242-6266acfe7048.png)
![Screen Shot 2022-07-17 at 10 03 21 PM](https://user-images.githubusercontent.com/1117327/179448299-81fe9b33-d046-45e7-bdbf-7d04d3f78e88.png)
![Screen Shot 2022-07-17 at 10 03 12 PM](https://user-images.githubusercontent.com/1117327/179448301-5196caee-a67c-45ce-b89c-21108d8068cd.png)

## Chapter 3 Day 1

1. In words, list 3 reasons why structs are different from resources.

Structs can be copied, resource can't.

Structs can be overwritte, resource can't.

Structs can be created anywhere but resources can only be created inside a contract.


2. Describe a situation where a resource might be better to use than a struct.

A NFT would be better represented as a resource than a struct.

3. What is the keyword to make a new resource?

`create`

4. Can a resource be created in a script or transaction (assuming there isn't a public function to create one)?

No, it can only be created inside a contract.

5. What is the type of the resource below?

```cadence
pub resource Jacob {

}
```

The resource is of type Jacob.

6. Let's play the "I Spy" game from when we were kids. I Spy 4 things wrong with this code. Please fix them.

```cadence
pub contract Test {

    // Hint: There's nothing wrong here ;)
    pub resource Jacob {
        pub let rocks: Bool
        init() {
            self.rocks = true
        }
    }

    pub fun createJacob(): @Jacob { // there is 1 here - Added @
        let myJacob <- create Jacob() // there are 2 here - Replaced = with <- and added Create
        return <- myJacob // there is 1 here - Fixed return value to <- myJacob
    }
}
```


## Chapter 3 Day 2

```
pub contract ResourceCollectionExample {

    pub var dictionaryOfNFTs: @{String: NFT}
    pub var arrayOfNFTs: @[NFT]


    pub resource NFT {
        pub let url: String
        init() {
            self.url = "http://someurl"
        }
    }

    pub fun addNFTToDict(nft: @NFT) {
        let key = nft.url
        let oldGreeting <- self.dictionaryOfNFTs[key] <- nft
        destroy oldGreeting
    }

    pub fun removeNFTFromDict(key: String): @NFT {
        let removedNft <- self.dictionaryOfNFTs.remove(key: key) ?? panic("Could not find the NFT!")
        return <- removedNft
    }

    pub fun addNFTToArray(nft: @NFT) {
        self.arrayOfNFTs.append(<- nft)
    }

    pub fun removeNFTFromArray(index: Int): @NFT {
        return <- self.arrayOfNFTs.remove(at: index)
    }


    init() {
        self.dictionaryOfNFTs <- {}
        self.arrayOfNFTs <- []
    }

}
```

## Chapter 3 Day 3

1. Define your own contract that stores a dictionary of resources. Add a function to get a reference to one of the resources in the dictionary.

```
pub contract ResourceCollectionExample {

    pub var dictionaryOfNFTs: @{String: NFT}
   

    pub resource NFT {
        pub let url: String
        init(_url: String) {
            self.url = _url
        }
    }

    pub fun getNFTReference(key: String): &NFT? {
        return &self.dictionaryOfNFTs[key] as &NFT?
    }

    init() {
        let url: String =  "www.youtube.com"
        self.dictionaryOfNFTs <- {
        url: <- create NFT(_url: url)
        }
    }
}
```

2. Create a script that reads information from that resource using the reference from the function you defined in part 1.

```
import ResourceCollectionExample from 0x01

pub fun main(): String {
  let ref = ResourceCollectionExample.getNFTReference(key: "www.youtube.cm")
  if (ref==nil) {
    log("NFT not found")
    return ""
  } else {
    log("NFT found")
    var nonNilRef = ref!
    return nonNilRef.url
  }
}
```

3. Explain, in your own words, why references can be useful in Cadence.

Reference help avoid moving resource and _refer_ to resource without needing to move it.
