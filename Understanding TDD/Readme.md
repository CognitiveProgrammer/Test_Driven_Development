# Module - 0 : Understanding TDD

### 1.1 Definition of TDD
*TDD can be defined as*

***TDD is a way of writing production code where test code for testing the production code is written in advance***

*As per the definition, TDD is used in production environment for writing* ***Unit Tests*** *before writing any production code*

### 1.2 4 Steps of doing TDD

*Doing TDD consists of 4 Steps*

***Step - 0 : Write enough test code (Including compile time and run time failures)***

*The word* ***enough*** *is subjective in mature, it depends upon individual and matures  with the passage of time. However its not advisable to write too much failing test code*

***Step - 1 : Write Production code to pass those failing Tests***

***Step - 2 : Re-Factor production code and verify the same with existing Tests***

***Step - 3 : Go to Step -1***

### 1.3 Who writes Tests in TDD and why only Unit Tests?

*TDD is a development only process, where tests must only be written by developers who are going to write the code too. TDD forces developers to think from usability perspective of the code and allows them to arrange their code accordingly. That's also the reason why TDD is sometimes also called Test Driven Design*

*TDD is not restricted to Unit Tests but its the most widely used arena. TDD can also be used for Integration functionality and System level Verification especially for UI related work, where exact nature of tests are available e.g Wireframe*
