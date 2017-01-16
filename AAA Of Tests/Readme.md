# Module - 1 : The AAA(Arrange-Act-Assert) of Unit Tests

## 2.1 Defining Unit Tests

*A piece of non production code written for testing a production unit of work. A unit test is* __Independent__ *in nature and should be able to run in isolation*

*A unit tests is divided into 3 parts which is collectively called as Arrange-Act-Assert*
***0. Arrange***
***1. Act***
***2. Assert***

## 2.2 Arrange

*The Arrange is used for making arrangements for tests to run, like instantiating stubs / mocks / fakes etc. The arrange phase is necessary because as per definition each unit tests are Independent in nature should be able to run in isolation.*

*To be able to achieve the said purpose of being independent and isolated, each unit tests need to arrange some environments for the tests to run. The* __Arrange__ *is meant for that purpose.*

## 2.3 Act

*Once the arrangements are done, the unit tests can execute to test the desired functionality. It may be call to a function / creation of objects / exception testing etc.*

## 2.4 Assert

*Once the unit tests are done, the* __Assert__ *is used for determining the whether the* __Act__ *produced intended results or not. Its the Assert phase that determines whether the test was successful or not*

## 2.5 Conclusion

*The idea of Arrange-Act-Assert act assert is independent of testing framework and is more of an arrangement than any coding practice*
