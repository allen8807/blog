# Fundamentals of Secure Development

* 课程目标

  * 辨识主要的软件安全因素。Identify major factors in the business, regulatory, and threat landscapes that drive the demand for software security.
  * 辨识重要的安全模型等。Identify important security models, standards, and guidelines that provide a strategic roadmap for application security.
  * 辨识软件开发流程中的安全实践和原则。Identify secure development practices and principles that correspond to each phase of the software development lifecycle.

* Module Overview模块概述

  * This module explains the overriding importance of software security and the potential business consequences of developing and deploying insecure software.讲述了软件安全的最高的重要性以及不安全的软件开发和部署带来的潜在业务结果

* Module Objectives模块目标

  * After completing this module, you’ll be able to:
    * Identify the difference between software security and network security.  认识到软件安全和网络安全的区别
    * Identify the business imperatives for software security, including:  认识到业务上对软件安全的必须性
      ```
      –   High business costs of security breaches. 安全漏洞的高额商业成本
      –   Compliance and legal implications of security breaches.  遵守和安全漏洞的法律影响
      –   Customer expectations of security.  用户的安全期待
      –   An increasing threat landscape. 不断增长的安全威胁远景
      ```

* What is Software Security?

  * Software security focuses on protecting information and resources made accessible by applications running on computer systems.软件安全是保护计算机应用可访问的信息和资源
  * Software security is often confused with network security. Network security focuses on the protection of an organization’s IT infrastructure—the servers and related equipment that control the flow of data between networked systems.网络安全是保护一个组织的IT基础设施，控制网络系统的数据流
  * Network security controls are typically insufficient to mitigate software security risks.网络安全控制通常不足以减轻软件安全风险
  * Software security attacks often occur at higher layers of operation, not visible to network security controls.软件安全攻击通常发生在较高层操作，对网络安全控制不可见。

* The Security Imperative

  * Key reasons why organizations must develop and deploy secure software include:
    * High business costs of security breaches
    * Compliance and legal implications of security breaches
    * Customer expectations of security
    * An increasing threat landscape

* The Business Costs of Software Security Breaches

  * Software security breaches expose organizations to various risks that result in the following direct and indirect costs:直接间接成本
    * Downtime and other operational losses if an application is hacked 停机时间和其他操作成本
    * Financial claims and settlements 财务索赔和结算
    * Compliance fines and penalties 合规罚款和处罚
    * Loss of investor and customer confidence 失去投资人和客户信心
    * Lost sales 销售额损失
    * Damage to reputation 声誉受损
  * McAfee estimates the global annual cost of cybercrime at over $400 billion dollars.\*
  * \*Source: Net Losses: Estimating the Global Cost of Cybercrime, June 2014, McAfee, Intel Security

* Compliance and Legal Implications 合规和法律意义

  * Federal and state regulations mandate software security and require protection of sensitive customer data. 法规要求保护用户敏感数据
  * Even if an organization is not required by local regulations to develop secure software, they might still need to do so to conduct business in other states.就算本地没有要求，要在其他地方开展业务也会有要求
  * It is difficult, if not impossible, to ignore software security without incurring significant fines or loss of business. 重大罚款和业务损失

* Customers Expect Secure Solutions 用户期望安全解决方案

  * Regulatory and legislative measures and the media have increased business awareness of the need for secure software and services. 监管，法规媒体提高了安全需求意识
  * Failure to develop and deliver secure software and services could damage your organization’s reputation, and drive business to your competitors. 失败的安全开发会影响声誉

* An Increasing Threat Landscape 增长的威胁环境

  * In the past, hackers were motivated to attack systems and software to gain notoriety. Today, the number of attacks is increasing, and attackers are motivated by financial gains, political agendas, and corporate and international espionage.黑客以前是为了名声，现在是为了财，政以及作为间谍
  * Specialized hacking techniques are publicly documented and well understood by many. In addition, automated attack tools are freely available and accessible.专业的黑客技术已经被公开，自动黑客工具也很容易免费得到
  * This translates to a higher probability of being hacked, as well as higher expected costs for recovering from cyber attacks.这些意味着攻击可能性的提高和恢复成本的提高

* Module Summary

  * In this module, you learned how software security differs from network security. 软件安全和网络安全的区别
  * You also learned the key reasons why organizations must develop secure software, including high business costs of security breaches, compliance and legal implications of security breaches, customer expectations of security, and a changing threat landscape. 为什么进行安全开发的关键原因

* Module Overview

  * This module introduces models, standards, and guidelines that you can use to improve the security posture of your applications. These resources provide a roadmap to follow to design security into your applications. You don't need to become a security expert to use them.

* Module Objectives

  * After completing this module, you will be able to:
    * Identify how security activities overlay the software development process.知道安全活动如何覆盖软件开发过程。
    * Identify the major models, standards, and guidelines of the application security industry, and how they can help you improve the security posture of your applications.知道应用程序安全行业的主要模型，标准和指南，以及它们如何帮助您提高应用程序的安全状态。

* Fundamentals of Secure Development

  * 作为开发，不需要成为安全专家，但是需要了解
  * 介绍一些安全标准和提高安全的快速方法
  * 但是关键在于保持对于安全知识的update，这些安全标准等能提高安全性，但不能让应用免疫于黑客攻击
  * SDLC，软件安全同样贯彻于软件生命周期的每一个过程中，Planning,Design,Development and Maintenacne,Implementation and Testing
  * 关注OWASP Top 10的安全问题，它们是最常见的10种web应用的攻击方式，要让应用不受这些影响
  * 微软的SDL流程，在每个阶段针对不同角色也有相关的安全性措施
  * CWE/SANS 25个最危险的软件错误，虽然是2011年的，但是对于现在依然有意义。
  * 支付行业有标准14条PA-DSS

    * 1. Do not retain full track data card verification code or PIN block data.
    * 1. Protect stored cardholder data.
    * 1. Provide secure authentication features.
    * 1. Log payment application activity.
    * 1. Develop secure payment applications.
    * 1. Protect wireless transmissions.
    * 1. Test payment applications to address vulnerabilities and maintain payment application updates.
    * 1. Facilitate secure network implementation.
    * 1. Do not allow cardholder data to be stored on a server connected to the Internet.
    * 1. Facilitate secure remote access to payment application.
    * 1. Encrypt sensitive traffic over public networks.
    * 1. Encrypt all non-console administrative access.
    * 1. Maintain a PA-DSS implementation guide for customers, resellers, and integrators.
    * 1. Assign PA-DSS responsibilities for personnel, and maintain training programs for personnel, 
         customers, resellers, and integrators.

  * Cloud Security Alliance \(CSA\) Notorious Nine Report 对云计算威胁最大的前9个的 报告

  * 2012年云安全联盟发布了10条大数据安全与挑战的报告

    * 1. Secure computations in distributed programming frameworks
    * 1. Security best practices for non-relational data stores
    * 1. Secure data storage and transactions logs
    * 1. Endpoint input validation/filtering
    * 1. Real-time security monitoring
    * 1. Scalable and composable privacy-preserving data mining and analytics
    * 1. Cryptographically enforced data-centric security
    * 1. Granular access control
    * 1. Granular audits
    * 1. Data provenance

  * OpenSAMM \(The Software Assurance Maturity Model\) 软件保证成熟度模型

  * BSIMM \(Building Security In Maturity Model\) 构建安全成熟度模型 不提供安全开发模型，提供参与组织的经验和课

  * BSIMM的安全框架SSF

  * Comprehensive Lightweight Application Security Process \(CLASP\) 是OWASP的一个产品。综合轻量级应用程序安全流程

  * The Common Criteria for Information Technology Security Evaluation \(CC\)信息技术安全评估的通用标准

  * In this module, you learned about the following secure development models, standards, and guidelines that help you efficiently improve your application security posture:

```
Open Web Application Security Project \(OWASP\) Top 10

Microsoft Security Development Lifecycle \(SDL\)

CWE/SANS Top 25 Most Dangerous Software Errors

Payment Application Data Security Standard \(PA-DSS\)

Cloud Security Alliance \(CSA\) Notorious Nine Report

Cloud Security Alliance \(CSA\) Top 10 Big Data Security and Privacy Challenges

OpenSAMM - Software Assurance Maturity Model \(SAMM\) 

Building Security In Maturity Model \(BSIMM\)

Comprehensive Lightweight Application Security Process \(CLASP\)

The Common Criteria for Information Technology Security Evaluation \(CC\) 



You learned that attacks and the techniques used to address them are constantly evolving, which requires you to stay current on the resources listed. You also learned that using these resources can greatly improve your application security posture, but it cannot make an application hacker proof or provide a guarantee of security.
```

* 把安全实践结合到各软件流程中去
* 介绍每个流程中的关键风险，自己结合到流程中去
* Planning阶段
  * 合法性的安全需求
  * 客户的安全需求
  * 安全培训
* 合法性方面建议有个了解全局的律师
* 客户安全方面了解要保护什么资产，要遵守什么，需要什么样的服务质量，什么数据是机密的



