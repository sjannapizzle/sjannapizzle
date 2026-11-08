# JP

Independent developer building on-chain research and low-latency trading infrastructure (Solana, EVM).

## Selected work (private repos — walkthrough on request)

**Cyclic-arbitrage engine for Robinhood Chain (Arbitrum Nitro), Rust**
- Custom Nitro node built for sub-millisecond execution, co-located with the bot.
- Custom feed infrastructure: own sequencer-feed relay in Rust (receive → timestamp → fan-out at ~1.4 µs per 52 KB message, zero-copy, no JSON parsing on the hot path), feed-to-head latency measured per message.
- In-memory pool state for Uniswap v2/v3/v4-style pools: TickMath/SqrtPriceMath/SwapMath reimplemented bit-exact against the chain, state advanced from receipts with per-swap verification.
- Per-block decision engine: cycle enumeration over ~10k pools, provably loss-free pre-filter (closed-form, ~50 ns), size optimisation per route; deterministic replay that reproduces every decision bit-identically.
- Execution path: allocation-free signing and raw HTTP/1.1 sending, profiled down to the µs.
- Market study over 50M swaps: capture rates, opportunity lifetimes, competitor mapping.

**Solana arbitrage & MEV research**
- Own parquet/DuckDB warehouse of DEX trades, transfers and liquidity events across all major venues.
- Atomic-arbitrage detection per epoch, trigger → backrun latency per slot, on-chain net P&L per searcher after priority fees, tips and failed transactions.

**Other:** Base trade warehouse; Zonnescan, a per-roof solar yield calculator for installers.

Python for research, Rust for execution.
