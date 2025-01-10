# Uniswap v4 Hooks Examples

This repository contains example implementations of Uniswap v4 hooks demonstrating advanced DeFi functionality. It includes two main hooks: Take Profits Hook and Points Hook.

## Overview

### Take Profits Hook

A smart contract that enables limit order-like functionality for taking profits at specified price points in Uniswap v4 pools.

### Points Hook

A rewards system that distributes points to users who provide liquidity or trade in specific pools, with additional referral mechanics.

## Core Concepts

### Take Profits Hook

#### Key Features

- Place limit orders at specific price points (ticks)
- Automatic order execution when price crosses specified ticks
- ERC1155-based position management
- Support for both trading directions (token0 → token1 and token1 → token0)
- Multiple orders at different price points
- Partial order execution and cancellation

#### Take Profits Implementation

1. Order Placement

   - Validates tick spacing
   - Transfers input tokens
   - Mints ERC1155 claim tokens
   - Updates pending orders

2. Order Execution

   - Monitors price changes via afterSwap
   - Executes matching orders
   - Updates claimable balances
   - Handles token settlements

3. Position Management
   - Unique position IDs per pool/tick/direction
   - Claim token accounting
   - Order cancellation logic

### Points Hook

#### Key Features

- Rewards for liquidity provision and trading
- Referral system with bonus points
- Native ETH pool integration
- Automatic point distribution
- ERC20-based points token

#### Points Implementation

1. Reward Distribution

   - Tracks user referrals
   - Calculates points based on activity
   - Handles referral bonuses

2. Activity Monitoring

   - afterSwap hook for trade rewards
   - afterAddLiquidity for LP rewards
   - ETH amount tracking

## Testing

### Take Profits Tests

- Order placement and cancellation
- Single and multiple order execution
- Direction-specific order execution
- Edge cases and token accounting

### Points Tests

- Basic point distribution
- Referral system
- Liquidity provision rewards
- Swap rewards

## Security Considerations

- Access control via onlyByPoolManager
- Safe token transfer handling
- Proper accounting and state management
- Input validation
- Reentrancy protection

## Dependencies

- Uniswap v4 Core & Periphery
- OpenZeppelin Contracts
- Solmate
- Forge Standard Library
