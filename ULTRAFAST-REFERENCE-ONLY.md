# UltraFast Reference Only

This fork is a research/reference copy of `JakedUp/Syncler-Packages`.

## Hard separation boundary

This repository is **not** the UltraFast production application and must not be merged into `djmer38/ultrafast-orion-torbox-private` as a repository or package.

It must not deploy the UltraFast Cloudflare Worker, change the UltraFast Worker name, change `PRIVATE_PATH`, change the Syncler vendor URL, change the UltraFast package ID, or contain UltraFast production secrets.

## Allowed use

Use this fork to study provider-package ideas, Jackett integration behavior, provider lists, deduplication concepts, and Syncler package conventions. Any useful concept must be independently reviewed, rewritten where appropriate, security-tested, and introduced to UltraFast through its own feature branch and pull request.

## Jackett credential rule

The upstream configurator accepts `jackett-base-url` and `jackett-api-key` as generated URL query parameters. UltraFast must **not** copy that credential pattern.

UltraFast's design keeps the Jackett API key in Cloudflare secret storage and reaches Jackett through a fixed private service binding. Syncler must never receive the Jackett API key.

## Provider safety rule

Do not automatically import every provider from this fork. Candidates must be individually evaluated for current availability, HTTPS, access terms, stability, response format, duplicate rate, latency, and actual incremental TorBox-cached coverage. Do not implement CAPTCHA bypass, access-control bypass, rate-limit evasion, anti-bot circumvention, or arbitrary proxying.

## Production rule

UltraFast remains the production boundary:

`Syncler -> existing UltraFast URL -> Orion primary -> optional Jackett fallback -> TorBox cache verification -> UltraFast filters/ranking -> Syncler`

The existing UltraFast URL and package identity remain authoritative.