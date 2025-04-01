# Awesome Mail Server Providers [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> \[!CAUTION]
> **Notice of Non-Affiliation and Disclaimer:** We are not affiliated, associated, authorized, endorsed by, or in any way officially connected with any provider, or any of their subsidiaries or its affiliates. The providers' name(s) as well as related names, marks, emblems, and images are registered trademarks of their respective owners.  The data and information shown on this page may be inaccurate or out of date.  If you have a suggestion or find statements or data to be inaccurate, then please submit a pull request or file an issue on GitHub.


## Table of Contents

* [Introduction](#introduction)
* [VPS and Dedicated Mail Server Provider Comparison Table](#vps-and-dedicated-mail-server-provider-comparison-table)
* [Mail Server Specific Features](#mail-server-specific-features)
  * [Reverse PTR Records](#reverse-ptr-records)
  * [IPv6 Support](#ipv6-support)
  * [Port 25 Restrictions](#port-25-restrictions)
* [Server Locations](#server-locations)
* [Pricing Tiers](#pricing-tiers)
  * [Entry Level Plans](#entry-level-plans)
  * [Mid-Range Plans](#mid-range-plans)
* [Security History](#security-history)
* [Analysis and Recommendations](#analysis-and-recommendations)
  * [Best Overall VPS Providers for Mail Servers](#best-overall-vps-providers-for-mail-servers)
  * [Best Budget Options](#best-budget-options)
  * [Best for High Volume Email](#best-for-high-volume-email)
  * [Considerations for Mail Server Hosting](#considerations-for-mail-server-hosting)
* [Conclusion](#conclusion)
* [References](#references)


## Introduction

This document provides a comprehensive comparison of VPS providers for hosting mail servers (SMTP servers).

The comparison focuses on key factors relevant to mail server operations, including pricing, features, server locations, and most importantly, mail server specific requirements such as reverse PTR records, IPv6 support, and port 25 restrictions.

> \[!TIP]
> You can set up your own mail server with a self-hosted mail server project, a custom domain name, and a VPS/Dedicated Mail Server provider.

1. **Self-Hosted Mail Server Projects:** We recommend [Forward Email](https://forwardemail.net) as the preferred self-hosted mail server project to use on your server (you can [self-host our entire codebase](https://github.com/orgs/forwardemail/discussions/300), however our service is cheaper to simply subscribe to than most providers at only $3/mo – and you can set up your custom domain in seconds!).  You may find others at <https://github.com/awesome-selfhosted/awesome-selfhosted> and <https://github.com/Mindbaz/awesome-opensource-email>.

2. **Custom Domain Name Requirement:** You will need a custom domain name in order to use a self-hosted mail server in combination with a provider listed below.  We recommend using <https://www.cloudflare.com/products/registrar/>, <https://tld-list.com/>, <https://namecheap.com>, and <https://domainr.com/> as resources and providers for finding your custom domain.

3. **VPS/Dedicated Mail Server Provider:** [See the comparison table below](#vps-and-dedicated-mail-server-provider-comparison-table) :point\_down:


## VPS and Dedicated Mail Server Provider Comparison Table

| Provider         | Lowest Price | RAM Range    | vCPU Range | Storage Range   | Transfer    | Reverse PTR | IPv6 | Port 25                         | Security History                      |
| ---------------- | ------------ | ------------ | ---------- | --------------- | ----------- | ----------- | ---- | ------------------------------- | ------------------------------------- |
| [Vultr][]        | $2.50/mo     | 512MB-64GB+  | 1-32+      | 10GB-1TB+ SSD   | 0.5TB-10TB+ | Yes         | Yes  | Blocked by default, can request | No major incidents                    |
| [DigitalOcean][] | $5/mo        | 1GB-64GB+    | 1-32+      | 25GB-1TB+ SSD   | 1TB-10TB+   | Yes         | Yes  | Blocked by default, can request | No major breaches                     |
| [Linode][]       | $5/mo        | 1GB-64GB+    | 1-32+      | 25GB-1TB+ SSD   | 1TB-10TB+   | Yes         | Yes  | Open by default                 | Multiple breaches (2013, 2016)        |
| [Hetzner][]      | €3.70/mo     | 2GB-64GB+    | 1-32+      | 20GB-1TB+ SSD   | 20TB-30TB+  | Yes         | Yes  | Open, but IPs often blacklisted | No major breaches                     |
| [RackNerd][]     | $11/yr       | 0.75GB-32GB+ | 1-16+      | 12GB-500GB+ SSD | 1TB-10TB+   | Yes         | Yes  | Open by default                 | No major incidents                    |
| [DataPacket][]   | $5/mo        | 1GB-64GB+    | 1-32+      | 25GB-1TB+ SSD   | 2TB-20TB+   | Yes         | Yes  | Open by default                 | No major incidents                    |
| [DartNode][]     | $2.95/mo     | 1GB-32GB+    | 1-16+      | 20GB-500GB+ SSD | Unlimited   | Yes         | Yes  | Open by default                 | No major incidents, newer provider    |
| [UltaHost][]     | $3.99/mo     | 1GB-32GB+    | 1-16+      | 20GB-500GB+ SSD | 1TB-10TB+   | Yes         | Yes  | Open, 200 emails/hour limit     | No major incidents                    |
| [Contabo][]      | €4.99/mo     | 4GB-64GB+    | 2-32+      | 50GB-1TB+ SSD   | Unlimited   | Yes         | Yes  | Open, 25 emails/minute limit    | No major incidents                    |
| [Hostinger][]    | $3.99/mo     | 1GB-32GB+    | 1-16+      | 20GB-500GB+ SSD | 1TB-10TB+   | Yes         | Yes  | Open, 5 emails/minute limit     | 2020 breach (shared hosting)          |
| [RareCloud][]    | $3.99/mo     | 1GB-32GB+    | 1-16+      | 25GB-500GB+ SSD | 2TB-10TB+   | Yes         | Yes  | Open by default                 | No major incidents, newer provider    |
| [OVH][]          | $3.35/mo     | 2GB-64GB+    | 1-32+      | 20GB-1TB+ SSD   | 10TB+       | Yes         | Yes  | Open by default                 | 2021 data center fire, network outage |


## Mail Server Specific Features

### Reverse PTR Records

Reverse PTR records are critical for mail server operations for the following reasons:

* Authentication and verification of sending servers
* Improved email deliverability
* Spam prevention
* Compliance with email standards

All providers in this comparison support configurable reverse PTR records, which is essential for running a mail server. The process for setting up PTR records varies by provider:

| Provider         | PTR Record Configuration    | Notes                       |
| ---------------- | --------------------------- | --------------------------- |
| [Vultr][]        | Via control panel           | Easy to configure           |
| [DigitalOcean][] | Via control panel           | Simple interface            |
| [Linode][]       | Via control panel           | Well-documented process     |
| [Hetzner][]      | Via control panel           | Straightforward setup       |
| [RackNerd][]     | Via control panel           | Quick configuration         |
| [DataPacket][]   | Via control panel           | Standard process            |
| [DartNode][]     | Directly on network manager | Unique direct configuration |
| [UltaHost][]     | Via control panel           | User-friendly interface     |
| [Contabo][]      | Via control panel           | Well-documented             |
| [Hostinger][]    | Via control panel           | Simple process              |
| [RareCloud][]    | Via control panel           | Standard configuration      |
| [OVH][]          | Via control panel           | Comprehensive documentation |

### IPv6 Support

IPv6 support is becoming increasingly important for mail servers due to:

* Future-proofing as IPv4 addresses become scarce
* Improved routing efficiency
* Enhanced security features
* Compliance with modern standards

All providers in this comparison offer IPv6 support on all their plans, which is beneficial for mail server operations. However, implementation quality may vary:

| Provider         | IPv6 Implementation | Notes                     |
| ---------------- | ------------------- | ------------------------- |
| [Vultr][]        | Full support        | Native implementation     |
| [DigitalOcean][] | Full support        | Available on all droplets |
| [Linode][]       | Full support        | Well-integrated           |
| [Hetzner][]      | Full support        | Reliable implementation   |
| [RackNerd][]     | Full support        | Standard implementation   |
| [DataPacket][]   | Full support        | Comprehensive support     |
| [DartNode][]     | Full support        | Modern implementation     |
| [UltaHost][]     | Full support        | Standard implementation   |
| [Contabo][]      | Full support        | Well-documented           |
| [Hostinger][]    | Full support        | Standard implementation   |
| [RareCloud][]    | Full support        | Modern implementation     |
| [OVH][]          | Full support        | Comprehensive support     |

### Port 25 Restrictions

Port 25 is the standard SMTP port used for email transmission. Many providers block or restrict this port to prevent spam. This is a critical consideration for mail server hosting:

| Provider         | Port 25 Status     | Email Sending Limits | Notes                                                                       |
| ---------------- | ------------------ | -------------------- | --------------------------------------------------------------------------- |
| [Vultr][]        | Blocked by default | Varies by plan       | Can be opened upon request with account verification                        |
| [DigitalOcean][] | Blocked by default | Varies by plan       | Can be opened by contacting support with business justification             |
| [Linode][]       | Open by default    | No specific limits   | Subject to anti-spam monitoring                                             |
| [Hetzner][]      | Open by default    | No specific limits   | Many IPs are blocked by major email providers due to historical spam issues |
| [RackNerd][]     | Open by default    | Unlimited            | No restrictions mentioned                                                   |
| [DataPacket][]   | Open by default    | No specific limits   | Subject to anti-abuse monitoring                                            |
| [DartNode][]     | Open by default    | Unlimited            | No restrictions mentioned                                                   |
| [UltaHost][]     | Open by default    | 200 emails/hour      | Moderate sending limit                                                      |
| [Contabo][]      | Open by default    | 25 emails/minute     | Reasonable sending limit                                                    |
| [Hostinger][]    | Open by default    | 5 emails/minute      | Very restrictive sending limit                                              |
| [RareCloud][]    | Open by default    | No specific limits   | No restrictions mentioned                                                   |
| [OVH][]          | Open by default    | No specific limits   | Subject to anti-spam monitoring                                             |


## Server Locations

Geographic distribution of servers is important for mail delivery speed and compliance with regional data regulations:

| Provider         | North America        | Europe                 | Asia       | Australia | South America | Africa |
| ---------------- | -------------------- | ---------------------- | ---------- | --------- | ------------- | ------ |
| [Vultr][]        | US (9 locations), CA | UK, NL, FR, DE, PL     | JP, SG, KR | AU (2)    | BR            | -      |
| [DigitalOcean][] | US (3), CA           | NL, UK, DE             | IN, SG     | AU        | -             | ZA     |
| [Linode][]       | US (6), CA           | UK, DE, NL, SE, PL, IT | JP, SG, IN | AU        | -             | ZA     |
| [Hetzner][]      | US (2)               | DE (2), FI             | -          | -         | -             | -      |
| [RackNerd][]     | US (6), CA           | NL                     | -          | -         | -             | -      |
| [DataPacket][]   | US (3)               | NL, DE, UK, CZ, PL     | SG, JP     | AU        | BR            | -      |
| [DartNode][]     | US (TX)              | -                      | -          | -         | -             | -      |
| [UltaHost][]     | US (2)               | DE, NL, UK             | SG         | AU        | -             | -      |
| [Contabo][]      | US (2)               | DE (2), UK, ES         | SG, JP     | AU        | -             | -      |
| [Hostinger][]    | US                   | UK, NL, LT             | SG         | -         | BR            | -      |
| [RareCloud][]    | US (2)               | DE, NL                 | SG         | -         | -             | -      |
| [OVH][]          | US, CA               | FR, UK, DE, PL, ES     | SG         | AU        | -             | -      |


## Pricing Tiers

### Entry Level Plans

| Provider         | Entry Price | RAM    | vCPU | Storage  | Transfer  |
| ---------------- | ----------- | ------ | ---- | -------- | --------- |
| [Vultr][]        | $2.50/mo    | 512MB  | 1    | 10GB SSD | 0.5TB     |
| [DigitalOcean][] | $5/mo       | 1GB    | 1    | 25GB SSD | 1TB       |
| [Linode][]       | $5/mo       | 1GB    | 1    | 25GB SSD | 1TB       |
| [Hetzner][]      | €3.70/mo    | 2GB    | 1    | 20GB SSD | 20TB      |
| [RackNerd][]     | $11/yr      | 0.75GB | 1    | 12GB SSD | 1TB       |
| [DataPacket][]   | $5/mo       | 1GB    | 1    | 25GB SSD | 2TB       |
| [DartNode][]     | $2.95/mo    | 1GB    | 1    | 20GB SSD | Unlimited |
| [UltaHost][]     | $3.99/mo    | 1GB    | 1    | 20GB SSD | 1TB       |
| [Contabo][]      | €4.99/mo    | 4GB    | 2    | 50GB SSD | Unlimited |
| [Hostinger][]    | $3.99/mo    | 1GB    | 1    | 20GB SSD | 1TB       |
| [RareCloud][]    | $3.99/mo    | 1GB    | 1    | 25GB SSD | 2TB       |
| [OVH][]          | $3.35/mo    | 2GB    | 1    | 20GB SSD | 10TB      |

### Mid-Range Plans

| Provider         | Mid-Range Price | RAM   | vCPU | Storage   | Transfer  |
| ---------------- | --------------- | ----- | ---- | --------- | --------- |
| [Vultr][]        | $10/mo          | 2GB   | 1    | 55GB SSD  | 2TB       |
| [DigitalOcean][] | $15/mo          | 2GB   | 2    | 60GB SSD  | 3TB       |
| [Linode][]       | $20/mo          | 4GB   | 2    | 80GB SSD  | 4TB       |
| [Hetzner][]      | €11.83/mo       | 8GB   | 2    | 80GB SSD  | 20TB      |
| [RackNerd][]     | $24/yr          | 2.5GB | 3    | 40GB SSD  | 6.5TB     |
| [DataPacket][]   | $20/mo          | 4GB   | 2    | 80GB SSD  | 10TB      |
| [DartNode][]     | $9.95/mo        | 4GB   | 2    | 80GB SSD  | Unlimited |
| [UltaHost][]     | $15.99/mo       | 4GB   | 2    | 80GB SSD  | 4TB       |
| [Contabo][]      | €8.99/mo        | 8GB   | 4    | 200GB SSD | Unlimited |
| [Hostinger][]    | $8.99/mo        | 4GB   | 2    | 80GB SSD  | 4TB       |
| [RareCloud][]    | $15.99/mo       | 4GB   | 4    | 80GB SSD  | 6TB       |
| [OVH][]          | $13.87/mo       | 8GB   | 2    | 80GB SSD  | 10TB      |


## Security History

Security history is a critical consideration when choosing a VPS provider for mail server hosting:

| Provider         | Major Security Incidents       | Notes                                                                                                            |
| ---------------- | ------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| [Vultr][]        | None publicly reported         | Good reputation for security                                                                                     |
| [DigitalOcean][] | None publicly reported         | Some reported incidents of account suspensions without warning                                                   |
| [Linode][]       | Multiple breaches (2013, 2016) | 2013: Credit card and password leak; 2016: User credentials found on external machine; DDoS attacks in 2015/2016 |
| [Hetzner][]      | None publicly reported         | Some IPs blacklisted by email providers due to historical spam issues                                            |
| [RackNerd][]     | None publicly reported         | Relatively newer provider compared to others                                                                     |
| [DataPacket][]   | None publicly reported         | Maintains strong network security practices                                                                      |
| [DartNode][]     | None publicly reported         | Relatively new provider with limited public security history                                                     |
| [UltaHost][]     | None publicly reported         | Regular security updates and monitoring                                                                          |
| [Contabo][]      | None publicly reported         | Strong reputation for security practices                                                                         |
| [Hostinger][]    | 2020 data breach               | Affected shared hosting database, VPS services reportedly not affected                                           |
| [RareCloud][]    | None publicly reported         | Relatively new provider with limited public security history                                                     |
| [OVH][]          | 2021 incidents                 | Major fire at SBG2 data center; Network misconfiguration causing global outage                                   |


## Analysis and Recommendations

### Best Overall VPS Providers for Mail Servers

1. **[RackNerd][]**: Offers open port 25 by default with unlimited outbound email, affordable yearly pricing, and good PTR record support.

2. **[Contabo][]**: Provides exceptional value with generous resources (4GB RAM at entry level), open port 25 with reasonable sending limits, and strong security history.

3. **[Linode][]**: Despite past security incidents, offers reliable mail server support with open port 25 by default and excellent documentation.

### Best Budget Options

1. **[RackNerd][]**: At $11/year for the entry plan, it's the most cost-effective option with mail server friendly features.

2. **[DartNode][]**: Starting at $2.95/month with unlimited bandwidth and open port 25, it's an excellent budget choice.

3. **[Vultr][]**: Starting at $2.50/month, though port 25 is blocked by default and requires verification to open.

### Best for High Volume Email

1. **[RackNerd][]**: Unlimited outbound email with open port 25 makes it ideal for high volume sending.

2. **[DartNode][]**: No specific sending limits mentioned and unlimited bandwidth.

3. **[Contabo][]**: 25 emails/minute limit (1,500/hour) is suitable for moderate to high volume.

### Considerations for Mail Server Hosting

When selecting a VPS provider for mail server hosting, consider:

1. **Port 25 Status**: Providers with open port 25 by default ([RackNerd][], [DartNode][], [Linode][], [Contabo][]) are preferable for easier setup.

2. **Email Sending Limits**: Consider your expected email volume and choose a provider with appropriate limits.

3. **IP Reputation**: Some providers (like [DigitalOcean][] and [Hetzner][]) may have IPs that are more likely to be blacklisted due to historical spam issues. After being allocated an IP address from a provider, **you should check its reputation** (e.g. on Spamhaus, Barracuda, ... – see our guide here for more insight: <https://forwardemail.net/faq#why-are-my-emails-landing-in-spam-and-junk-and-how-can-i-check-my-domain-reputation>).

4. **Security History**: Providers with clean security records are generally preferable for handling sensitive email data.

5. **Geographic Distribution**: Choose a provider with server locations that match your target audience for better delivery performance.


## Conclusion

All providers in this comparison support the essential mail server requirements of configurable reverse PTR records and IPv6. The main differentiating factors are port 25 restrictions, email sending limits, pricing, and security history.  You may find that Reddit, LowEndTalk, and other discussion websites contain more information specific to a provider or a topic (e.g. `site:lowendtalk.com port 25` might be a good search query for port 25 restrictions).

For most mail server use cases, [RackNerd][], [Contabo][], and [Linode][] offer the best balance of features, price, and mail server compatibility. However, specific needs regarding budget, email volume, and geographic distribution may make other providers more suitable for particular use cases.

Our team uses [DataPacket][] and previously used [DigitalOcean][] and [Vultr][].  We operate baremetal servers with custom AMD Ryzen hardware, NVMe SSD drives, LUKS encryption, and more. You can learn more about how and why we chose DataPacket on this Privacy Guides discussion thread: <https://discuss.privacyguides.net/t/forward-email-new-features/24845/45>


## References

1. <https://github.com/hiddify/awesome-freedom/blob/main/vps-providers.md>
2. <https://github.com/leogallego/awesome-vps-price-breakdown>
3. <https://gist.github.com/justjanne/205cc548148829078d4bf2fd394f50ae>
4. <https://webshanks.com/vps-with-open-port-25/>
5. <https://www.cloudflare.com/learning/dns/dns-records/dns-ptr-record/>
6. <https://www.rapidseedbox.com/blog/ipv6-email-infrastructure>
7. <https://wptavern.com/linode-confirms-data-security-breach-that-matches-recent-wp-engine-attack>
8. Provider official websites (pricing and feature information)

[vultr]: https://www.vultr.com/?ref=7429848

[digitalocean]: https://m.do.co/c/a7fe489d1b27

[linode]: https://www.linode.com/?ref=forwardemail_dot_net

[hetzner]: https://www.hetzner.com/?ref=forwardemail_dot_net

[racknerd]: https://www.racknerd.com/?ref=forwardemail_dot_net

[datapacket]: https://www.datapacket.com/?ref=forwardemail_dot_net

[dartnode]: https://dartnode.com/?ref=forwardemail_dot_net

[ultahost]: https://ultahost.com/?ref=forwardemail_dot_net

[contabo]: https://contabo.com/en-us/?ref=forwardemail_dot_net

[hostinger]: https://www.hostinger.com/?ref=forwardemail_dot_net

[rarecloud]: https://rarecloud.io/?ref=forwardemail_dot_net

[ovh]: https://us.ovhcloud.com/?ref=forwardemail_dot_net
