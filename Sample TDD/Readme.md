# Module - 3 : A Sample TDD Code in C++ language

## 1.1 Using Google Test Framework
*For demonstration purpose, we'll will be using Google Test Framework. More details about Google Test Framework can be found HERE(https://github.com/google/googletest)*

## 1.2 4 Code Creation

*Before we can test something, we need to have a code for testing. Here we're writing a simple class which takes an input parameter while being constructed and then the test verifies that the class contains the same data all during its lifetime*

```
class MyTest {
	unsigned int internalValue;
public:
	MyTest(int externalValue) : internalValue(externalValue) {}
	unsigned int GetInternalValue() const {
		return internalValue;
	}
};

```
## 1.3 Writing Arrange-Act-Assert Unit Test

*The unit tests for testing the value shall be arranged as below*

```
TEST(CheckClass, CheckValue) {
	// Arrange
	unsigned int testValue = 200;

	// Act
	MyTest mTestInstance(testValue);

	// Assert
	EXPECT_EQ(mTestInstance.GetInternalValue(), testValue);

}

```
*Here we're first arranging what environment we need to test like having a variable with a predefined value. Then we move on to Act where create the instance of the class using the environment we created in Arrange i.e using testValue*

*Once the code in Act executes, we then move on to assert whether the test is successful or not. Its the assert phase which will determine whether the test is successful or not.

__Remember that the test is independent and isolated. It can run multiple times without impacting the results based on any of its earlier runs__
