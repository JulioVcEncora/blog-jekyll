---
layout: post
title: Answering questions about one Open Source Project
--- 


OSS Questions 

This week I chose to answer the question regarding Mockito library, specifically the one that says, “How does the mock() method works?”. 
 
The answer to this question involves two parts, how does it work internally and how anyone can implement it.  
 
To answer the first part (how does it work internally), the mock method uses Java’s Proxy class to create a dynamic proxy object which extends or implements the provided interfaces. Having answered this, the mock method needs an interface as an argument to create a mock object. Ex. Mockito.mock(ClassName.class). 

After having set the mock function with the specified interface we can expect a default behavior for each one of the methods of the interface to return a 0 or null, if we want them to behave as they must do we must “stub” them so that we can get the expected answer. Mockito refers to “stub” when we add the when() method and the thenReturn() method, when applied they will look like this “Mockito.when(mockedObject.interfaceMethod(argument)).thenReturn(expectedResult)”. The mockedObject is the name we give to the mock function with the specified interface, the interfaceMethod is the name of one of the interface methods. We can also verify the mocked objects and use matchers to fully test our mocked object. 
 
For the projects I chose, I decided to work with react-native and Selenium, I chose react-native since I’m pretty interested in being able to develop mobile apps for any operating system, and I chose selenium since it is a pretty popular suite for automating a browser. 
 
1. React Native Question – How does StyleSheet.create() creates styles for components and what is the differences for using inline styles?  
 
2. Selenium Question – When we use a WebDriver what is the difference between driver.findElement(By.id(“elementId)) and driver.findElement(By.cssSelector(“#elementId”))? 
