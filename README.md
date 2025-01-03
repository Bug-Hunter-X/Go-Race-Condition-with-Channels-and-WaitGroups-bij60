# Go Race Condition with Channels and WaitGroups

This repository demonstrates a subtle race condition in a Go program that uses channels and WaitGroups. The code appears correct at first glance but can lead to unpredictable behavior, particularly in concurrent environments.

The `bug.go` file contains the buggy code. The `bugSolution.go` file offers a corrected version.  This example highlights the importance of careful channel handling in Go concurrency.

## Bug Description

A race condition exists due to the order in which goroutines might execute. The `close(ch)` call in the first goroutine is not guaranteed to happen before the second goroutine attempts to read from `ch` after it is closed.  This could cause a runtime panic.