Vending Machine Controller IP Verification

Project Overview

This repository contains the UVM-based verification environment for the Vending Machine Controller (VMC) IP. The DUT is a configurable vending machine controller that supports multiple items, currencies, and operational modes. The verification environment ensures the DUT operates correctly under normal, corner-case, and stress scenarios.

Project Objectives Verify reset behavior and initialization sequences. Validate APB-based configuration for read/write operations. Confirm dispense logic and change calculation under all scenarios. Handle error cases such as invalid items, unsupported currencies, underpayment, or out-of-stock conditions. Achieve full functional coverage for robust and reliable design.

Verification Architecture Methodology: Universal Verification Methodology (UVM)

Language: SV

<img width="292" height="542" alt="image" src="https://github.com/user-attachments/assets/5d17a5d1-e618-4b3e-9537-68135679a6c1" />

UVM

Agents and Responsibilities:

cfg_agent → Handles APB-based register read/write and configuration.

currency_agent → Simulates currency insertion events.

item_agent → Simulates user item selection.

dispense_agent → Monitors output and validates dispense and change logic.

Scoreboard & Checkers → Compare DUT outputs with reference model results.

Assertions → Verify FSM behavior and APB protocol compliance.

APB Interface Verification

The APB (Advanced Peripheral Bus) interface ensures proper communication between the DUT and its controller.

Write Transactions: Verify correct data is written to registers and applied to DUT configuration.

Read Transactions: Validate accurate data retrieval from registers and correct status reporting.

Edge Case Testing: Ensure error handling for invalid addresses and unsupported operations.

Timing Compliance: Confirm transactions complete within specified cycles with proper handshake signals.

Test Categories

Reset & Initialization Tests – DUT behavior after reset.

Configuration Tests – APB read/write, edge cases, boundary values.

Operational Tests – Exact pay, overpay, underpay, multi-currency, stock validation.

Error Handling Tests – Invalid item, unsupported currency, underpayment, out-of-stock.

Randomized & Stress Tests – Randomized input sequences for robustness.

Timing Tests – Verify latency ≤10 cycles per transaction.

Bugs and Observations

pready signal declared but unused in DUT.

Missing synchronization for asynchronous currency clock domain.

FSM misbehavior when currency is inserted during configuration mode.

Multiple dispense pulses observed in stress scenarios.

APB write/read timing edge cases detected in initial simulations.

Key Highlights

Modular, reusable UVM agents.

Comprehensive functional and protocol coverage.

Multi-item, multi-currency support for real-world scenarios.

Scalable testbench architecture for future extensions.

Robust APB read/write verification ensuring reliable configuration.

Full code and testbench are available here on EDA Playground:https://edaplayground.com/x/6rrw
