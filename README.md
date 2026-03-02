# 🕷 Recommended Proxy Services 🕷

## 🇨🇳 中文
🌟 **OKKproxxy** — 爬虫代理轮换专家
- 🔥 完美适配Crawlee ProxyConfiguration，一行代码接入住宅IP池
- 🚀 自动轮换200+国家IP，每次请求不同出口，反爬无忧
- 🌐 覆盖全球200+国家和地区，9000万+住宅IP资源
- 💰 新用户充值加赠20%流量
- 🔗 [okkproxy.com](https://okkproxy.com)

🌟 **NIUproxxy** — 高并发采集加速器
- 🔥 针对Crawlee并发架构优化，支持数千并发连接不掉线
- 🚀 智能会话保持，同一任务绑定同一IP，数据一致性有保障
- 🌐 全球机房节点覆盖，就近接入延迟低至50ms
- 💰 新用户充值加赠20%流量
- 🔗 [niuproxy.com](https://niuproxy.com)

🌟 **COLAproxxy** — 性价比之选
- 🔥 按流量计费，不限并发数，小团队也能用得起住宅IP
- 🚀 兼容所有HTTP/SOCKS5代理协议，Crawlee零配置接入
- 🌐 覆盖190+国家，城市级定位精准采集
- 💰 新用户充值加赠20%流量
- 🔗 [colaproxy.com](https://colaproxy.com)

---
## 🇺🇸 English
🌟 **OKKproxxy** — Residential Proxy Rotation Expert
- 🔥 Crawlee ProxyConfiguration compatible, one-line integration
- 🚀 Auto-rotate 200+ countries IP, different exit IP per request
- 🌐 200+ countries coverage, 90M+ residential IPs
- 💰 20% bonus for new users
- 🔗 [okkproxy.com](https://okkproxy.com)

🌟 **NIUproxxy** — High-Concurrency Scraping Accelerator
- 🔥 Optimized for Crawlee architecture, supports thousands of concurrent connections
- 🚀 Smart session persistence, bind same IP to same task
- 🌐 Global data center nodes, latency as low as 50ms
- 💰 20% bonus for new users
- 🔗 [niuproxy.com](https://niuproxy.com)

🌟 **COLAproxxy** — Best Value Choice
- 🔥 Pay-per-traffic, unlimited concurrency, affordable for small teams
- 🚀 Compatible with all HTTP/SOCKS5 protocols, zero-config for Crawlee
- 🌐 190+ countries, city-level targeting
- 💰 20% bonus for new users
- 🔗 [colaproxy.com](https://colaproxy.com)

---

FireProx
==================
- [Overview](#overview)
	- [Benefits](#benefits)
	- [Disclaimers](#disclaimers)
- [Maintainer](#maintainer)
- [Credit](#credit)
- [Basic Usage](#basic-usage)
- [Installation](#installation)
- [Screenshots](#screenshots)
- [Contributing](#contributing)

## Overview ##
Being able to hide or continually rotate the source IP address when making web calls can be difficult or expensive. A number of tools have existed for some time but they were either limited with the number of IP addresses, were expensive, or required deployment of lots of VPS's. FireProx leverages the AWS API Gateway to create pass-through proxies that rotate the source IP address with every request! Use FireProx to create a proxy URL that points to a destination server and then make web requests to the proxy URL which returns the destination server response!

**Brought to you by:**

![Black Hills Information Security](https://www.blackhillsinfosec.com/wp-content/uploads/2016/03/BHIS-logo-L-300x300.png "Black Hills Information Security")

## Maintainer
- Follow me on Twitter for more tips, tricks, and tools (or just to say hi)! ([Mike Felch - @ustayready](https://twitter.com/ustayready)) 

### Benefits ##

 * Rotates IP address with every request
 * Configure separate regions
 * All HTTP methods supported
 * All parameters and URI's are passed through
 * Create, delete, list, or update proxies
 * Spoof X-Forwarded-For source IP header by requesting with an X-My-X-Forwarded-For header
 
 
### Disclaimers ##
 * ~~Source IP address is passed to the destination in the X-Forwarded-For header by AWS~~
   * ~~($100 to the first person to figure out how to strip it in the AWS config before it reaches the destination LOL!)~~
   * Thanks to ![Fred Reimer](https://github.com/freimer) for the awesome X-Forwarded-For patch within 1 hour!
 * I am not responsible if you don't abide by the robots.txt :)
 * CloudFlare seems to sometimes detect X-Forwarded-For when blocking scrapers (**NEED TO TEST W/ NEW PATCH**)
 * Use of this tool on systems other than those that you own are likely to violate the [AWS Acceptable Use Policy](https://aws.amazon.com/aup/) and could potentially lead to termination or suspension of your AWS account. Further, even use of this tool on systems that you do own, or have explicit permission to perform penetration testing on, is subject to the AWS policy on [penetration testing](https://aws.amazon.com/security/penetration-testing/).

## Credit ##
After releasing FireProx publicly, I learned two others were already using the AWS API Gateway technique. Researching the chain of events and having some great conversations, I came to the realization that the only reason I even knew about it was because of these people. I thought it would be cool to give them a few shout-outs and credit, follow these people -- they are awesome. 

Credit goes to [Ryan Hanson - @ryHanson](https://twitter.com/ryHanson) who is the first known source of the API Gateway technique

Shout-out to [Mike Hodges - @rmikehodges](https://twitter.com/rmikehodges) for making it public in ![hideNsneak](https://github.com/rmikehodges/hideNsneak) at BlackHat Arsenal 2018

Major shout-out, once again, to my good friend [Ralph May - @ralphte1](https://twitter.com/ralphte1) for introducing me to the technique awhile back.

## Basic Usage ##
### Requires AWS access key and secret access key or aws cli configured
usage: **fire.py** [-h] [--access_key ACCESS_KEY]
               [--secret_access_key SECRET_ACCESS_KEY] [--region REGION]
               [--command COMMAND] [--api_id API_ID] [--url URL]

FireProx API Gateway Manager
```
usage: fire.py [-h] [--profile_name PROFILE_NAME] [--access_key ACCESS_KEY] [--secret_access_key SECRET_ACCESS_KEY] [--session_token SESSION_TOKEN] [--region REGION] [--command COMMAND] [--api_id API_ID] [--url URL]

FireProx API Gateway Manager

optional arguments:
  -h, --help            show this help message and exit
  --profile_name PROFILE_NAME
                        AWS Profile Name to store/retrieve credentials
  --access_key ACCESS_KEY
                        AWS Access Key
  --secret_access_key SECRET_ACCESS_KEY
                        AWS Secret Access Key
  --session_token SESSION_TOKEN
                        AWS Session Token
  --region REGION       AWS Region
  --command COMMAND     Commands: list, create, delete, update
  --api_id API_ID       API ID
  --url URL             URL end-point
```

* Examples
	* examples/google.py: Use a FireProx proxy to scrape Google search.
	* examples/bing.py: Use a FireProx proxy to scrape Bing search.
         
## Installation ##
You can install and run with the following command:

```bash
$ git clone https://github.com/ustayready/fireprox
$ cd fireprox
~/fireprox$ virtualenv -p python3 .
~/fireprox$ source bin/activate
(fireprox) ~/fireprox$ pip install -r requirements.txt
(fireprox) ~/fireprox$ python fire.py
```

Note that Python 3.6 is required.

Building a Docker image: (Currently does not work on Docker for Windows, possibly due to line endings in entrypoint.sh.)
```bash
$ git clone https://github.com/ustayready/fireprox
$ cd fireprox
$ docker build -t fireprox .
$ docker run --rm -it fireprox -h
```

## Screenshots
![Usage](https://github.com/ustayready/fireprox/blob/master/screenshots/usage.png "usage")
![List](https://github.com/ustayready/fireprox/blob/master/screenshots/list.png "list")
![Create](https://github.com/ustayready/fireprox/blob/master/screenshots/create.png "create")
![Delete](https://github.com/ustayready/fireprox/blob/master/screenshots/delete.png "delete")
![Demo](https://github.com/ustayready/fireprox/blob/master/screenshots/demo.png "demo")

## Contributing

1. Create an issue to discuss your idea
2. Fork FireProx (https://github.com/ustayready/fireprox/fork)
3. Create your feature branch (`git checkout -b my-new-feature`)
4. Commit your changes (`git commit -am 'Add some feature'`)
5. Push to the branch (`git push origin my-new-feature`)
6. Create a new Pull Request

**Bug reports, feature requests and patches are welcome.**

