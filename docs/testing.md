---
sidebar_position: 1
---
# Testing Home

This is the Testing Home.

## Backlinks
* [[Define different variables for received and expected values in assertions]]
	* When writing assertions in [[Testing]] (TODO alias: tests), do not use the same variable reference as both the received and the expected value. This is because you may accidentally assert that a reference to a value is equal to itself. It can also make the test [[Readability]] (TODO alias: hard to understand) by obscuring what is happening in the test and cause unexpected failures. For example, if the reference value is changed unexpectedly.
* [[Home]]
	* [[Testing]]
