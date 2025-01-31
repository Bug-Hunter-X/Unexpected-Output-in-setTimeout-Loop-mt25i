# Unexpected Output in setTimeout Loop

This repository demonstrates a common JavaScript closure issue encountered when using `setTimeout` within a loop. The problem lies in how the loop variable `i` is captured by the callback function.  The expected behavior is to print 0 to 9 sequentially after one second intervals. However, due to the closure, all callbacks will access the final value of `i`, resulting in 10 being printed multiple times.

## Bug Description

The code uses a `for` loop to schedule multiple `setTimeout` calls.  Each callback should print the value of `i` at the time it was scheduled.  Due to the way closures work in JavaScript, this doesn't happen. The closure captures the variable, not its value at the time of creation.

## Solution

The solution involves creating a closure over a new variable using an immediately invoked function expression (IIFE) that encapsulates the loop variable `i` for each iteration.