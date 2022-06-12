# Class 06

## How to use the Random Module in Python

### What is Random Module

The random module provides access to functions that support many operations. Perhaps the most important thing is that it allows you to generate random numbers.

### When to use it?

We want the computer to pick a random number in a given range Pick a random element from a list, pick a random card from a deck, flip a coin etc. When making your password database more secure or powering a random page feature of your website.

### Random functions

* Randint
  * Functionality : return random integer,
  * Parameters :  lowest and a highest number.
  * Ex: random.randint(0, 5)
* Random
  * Functionality : If you want a larger number, you can multiply it.
  * Parameters: None.
  * Ex: random.random() * 100
* Choice
  * Functionality: Generate a random value from the sequence
  * Parameters: List of choices (Random element)
  * Ex: random.choice( ['red', 'black', 'green'] ).
* Shuffle
  * Functionality:  shuffles the elements in list in place, so they are in a random order.
  * Parameters: List
  * EX: x = [[i] for i in range(10)]
shuffle(x)
* Randrange
  * Functionality: Generate a randomly selected element from range.
  * Parameters: start, stop, step
  * Ex: random.randrange(start, stop[, step])

#### secrets — Generate secure random numbers for managing secrets
##### What is Secrets?
module is used for generating cryptographically strong random numbers suitable for managing data such as passwords, account authentication, security tokens, and related secrets.
<br/> 
_Used Case_
In particular, secrets should be used in preference to the default pseudo-random number generator in the random module, which is designed for modelling and simulation, not security or cryptography.
* Functions:
  * class secrets.SystemRandom
  * secrets.choice
  * secrets.randbelow(n)
  * secrets.randbits(k)
* Generating tokens
  * secrets.token_bytes([nbytes=None])
  * secrets.token_hex([nbytes=None])
  * secrets.token_urlsafe([nbytes=None])
  
## Risk Analysis

### What is Risk Analysis in Software Testing and how to perform it?

risk analysis is the process of identifying the risks in applications or software that you built and prioritizing them to test.

### Why use Risk Analysis?

using risk analysis at the beginning of a project highlights the potential problem areas. After knowing about the risk areas, it helps the developers and managers to mitigate the risks.

#### Risk magnitude indicators

* High: means the effect of the risk would be very high and non-tolerable. The company might face loss.

* Medium: it is tolerable but not desirable. The company may suffer financially but there is a limited risk.

* Low: it is tolerable. There lies little or no external exposure or no financial loss.

### Risk Identification

* Business Risks
* Testing Risks
* Premature Release Risk
* Software Risks

### The perspective of Risk Assessment

* Effect – To assess risk by Effect. In case you identify a condition, event or action and try to determine its impact.

* Cause – To assess risk by Cause is opposite of by Effect. Initialize scanning the problem and reach to the point that could be the most probable reason behind that.

* Likelihood – To assess risk by Likelihood is to say that there is a probability that a requirement won’t be satisfied.

### How to perform Risk Analysis?

1. Searching the risk

2. Analyzing the impact of each individual risk

3. Measures for the risk identified

## Dependency Injection
### What is Dependency Injection?
Is a technique whereby one object (or static method) supplies the dependencies of another object. A dependency is an object that can be used (a service).
### Small Definition: Dependency or dependent means relying on something for support
### Why should I use dependency injection?
We can think of DI as the middleman in our code who does all the work of creating the preferred tasks object and providing it to our class.

### Types of dependency injection:
1. constructor injection: the dependencies are provided through a class constructor.
2. setter injection: the client exposes a setter method that the injector uses to inject the dependency.
3. interface injection: the dependency provides an injector method that will inject the dependency into any client passed to it. 

### Dependency Injection’s Responsibility
* Create the objects
* Know which classes require those objects
* And provide them all those objects

### Inversion of control —the concept behind DI
This states that a class should not configure its dependencies statically but should be configured by some other class from outside.

### Benefits of using DI
* Helps in Unit testing.
* Boiler plate code is reduced, as initializing of dependencies is done by the injector component.
* Extending the application becomes easier.
* Helps to enable loose coupling, which is important in application programming.

### Disadvantages of DI
* It’s a bit complex to learn, and if overused can lead to management issues and other problems.
* Many compile time errors are pushed to run-time.
* Dependency injection frameworks are implemented with reflection or dynamic programming. This can hinder use of IDE automation, such as “find references”, “show call hierarchy” and safe refactoring.

### Libraries and Frameworks that implement DI
* Spring (Java)
* Google Guice (Java)
* Dagger (Java and Android)
* Castle Windsor (.NET)
* Unity(.NET)

## Notes: 
* dependencies can be injected at runtime rather than at compile time



## Resources
* [Dependency injection](https://www.freecodecamp.org/news/a-quick-intro-to-dependency-injection-what-it-is-and-when-to-use-it-7578c84fa88f/)
* [Random](https://docs.python.org/3/library/random.html)
* [How to use the Random Module in Python](https://www.pythonforbeginners.com/random/how-to-use-the-random-module-in-python)
* [Risk Analysis](https://www.edureka.co/blog/risk-analysis-in-software-testing/)






