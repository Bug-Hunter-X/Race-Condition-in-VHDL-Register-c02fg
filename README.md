# VHDL Race Condition Example

This repository demonstrates a potential race condition in a simple VHDL register.  The issue arises from the sensitivity list of the process and the timing relationship between `clk` and `data_in` signal updates.  The solution showcases a more robust approach using synchronous signal updates to prevent this issue.

## Bug Description

The provided VHDL code implements a simple register.  However, if the input data (`data_in`) changes very close to the rising edge of the clock, the updated value might not be captured reliably, leading to unexpected behavior.  This is especially true in high-speed designs where timing margins are tighter.

## Solution

The race condition can be avoided by ensuring that the signal updates are always synchronized with the clock. The `data_in` signal's changes are registered in a separate process which only captures its value on the rising edge of the clock.  This avoids the possibility of the `internal_data` receiving an incorrect value.