---
layout: post
microblog: true
audio: 
date: 2018-08-01 18:30:06 +0100
guid: http://lukas.micro.blog/2018/08/01/facebook-google-microsoft.html
---
Facebook, Google, Microsoft and Twitter recently announced the [Data Transfer Project](https://datatransferproject.dev/) (DTP) as a way to improve data portability between different services. Naturally, I was intrigued to understand what precisely the DTP is. So I spend a recent ride on the train riding [the whitepaper](https://datatransferproject.dev/dtp-overview.pdf) and will give you a little summary here:

DTP provides [a Java-based, Docker-deployable open source application](https://github.com/google/data-transfer-project) that executes bulk tasks with the following workflow:
* Authenticate with providers via OAuth.
* Export data from one provider through their API and, if necessary, convert it to a standard data model via adapters. Providers can write their own adapters, or third parties can contribute and share them as part of the open source project.
* Temporarily store data in encrypted form.
* Import data into another provider using their API after, if necessary, converting the standard data model back into the provider-specific format.

A running instance of DTP is called a host. There are different possible models for hosts. One option (_distributed_) is that a provider itself runs a DTP that allows import from and export to a list of other providers of their choosing. The second option (_centralized_) is a third party that hosts the infrastructure to exchange data between different providers. The DTP whitepaper suggests that Data Portability NGOs could run such an instance. Finally, the third option (_self-managed_) means end users are running their own DTP instance.

The DTP only provides software and doesn't specify any requirements for providers as to with who they have to interact. Every host decides which adapters it makes available and needs to apply for API access with each provider. Also, the whole design of the DTP is for one-time data transfer and does not support continuous synchronization.

**My opinion:** The DTP is convincing and can certainly help with data portability. Of course, it depends on providers opening up their APIs, although consumer demand and data portability requirements (as in the GDPR) could drive them. Its scope is limited, but I think its data models could be applied even outside this scope for federation and interoperability (or they could become ["just another standard ..."](https://xkcd.com/927/)).
