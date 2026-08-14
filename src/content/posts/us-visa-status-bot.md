---
title: 一个自动刷新美签状态的Bot
published: 2022-12-27
tags:
  - 科技
lang: zh
abbrlink: us-visa-status-bot
---

## 一个自动刷新美签状态的Bot

12月初我在加拿大申请美签。由于年末假期导致处理速度下降，即使是当场批准的签证，也要等待3天到两周的时间才能取回。官方的签证状态查询[网站](https://ceac.state.gov/CEACStatTracker/Status.aspx)十分老旧：
* 不提供状态追踪提醒的服务，导致申请者必须频繁的手动查询
* 网站不支持历史记录自动填写，所以每次查询都得重新选择签证类型，输入签证ID，签证位置和验证码

一番搜索之后，我发现了@lixin-wei的github项目[ceac_tracker](https://github.com/lixin-wei/ceac_tracker)。这个工具已经有了大部分我需要的功能
* 定期爬取签证状态
* 存储签证状态，一旦有变化就会发送通知

唯一美中不足的是它暂时只支持邮件，钉钉两种推送方式。在这个基础上，我利用[Discord Webhook](https://support.discord.com/hc/en-us/articles/228383668-Intro-to-Webhooks)，添加了在Discord频道推送的方式。最后，利用[Google Cloud](https://cloud.google.com/)虚拟机后台运行，我就得到了一个自动刷新美签状态的Bot
* 每十分钟查询我的美签状态，存入本地数据库并向Discord频道发送信息
* 假如美签状态变更，向Discord频道发送通知并且停止脚本

在脚本运行了24小时后，我的签证状态从Approved变成Issue。
![Issue!](/images/visa-status-bot.png)

最后，祝所有正在签，想要签，等签的朋友们一切顺利。

### Reference
1. [ceac_tracker](https://github.com/lixin-wei/ceac_tracker)@lixin-wei
2. My fork of [ceac_tracker](https://github.com/wuhao21/ceac_tracker)
3. [CREATE A DISCORD WEBHOOK WITH PYTHON FOR YOUR BOT](https://hackaday.com/2018/02/15/creating-a-discord-webhook-in-python/)