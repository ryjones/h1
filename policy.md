**NOTE:** None of the web sites run by The Linux Foundation or by the Hyperledger Foundation are eligible for the bounty. That means only the code *in* the Hyperledger Fabric codebase is eligible for the bounty.  Everything else, including our websites, are *not* in scope (e.g. JIRA, Gerrit, Rocket.Chat, homepage, and wiki).

**UPDATE:** We now have a free online course that covers all of the details of setting up a Hyperledger Fabric test network for analysis.  The link to the course is: https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS171x+3T2017/course/

Hyperledger is a global open source collaborative effort created to advance cross-industry blockchain technologies, hosted by The Linux Foundation, and developed by technologists in finance, banking, internet of things, supply chains, manufacturing and technology.

Because blockchain and distributed ledger technology has such a wide range of applications, ranging from critical infrastructure (e.g. energy markets, bank settlements, etc) to social systems (e.g. digital healthcare records, voting, etc) the Hyperledger community is eager to work with the broader security community to help identify any security vulnerabilities in the various Hyperledger technologies and report and fix them in a timely and responsible manner.

Because Hyperledger projects are in various stages of development and maturity, the community has chosen to limit our bug bounty program to those projects that have reached a “1.0” release maturity.  Additional projects will be joining the bug bounty in the near future, and we invite you to also review those when they join the bounty program.

The Hyperledger Foundation security team consists of volunteer open source developers that will make a best effort to respond to incoming reports within 2 business days and make a bounty determination after validating a legitimate security issue within 60 business days. Our transparency is greater than other organizations, however we are using a confidential vulnerability reporting and resolution system. We will do our best to keep you informed about our progress throughout the process and per our security policy, all vulnerabilities will be disclosed responsibly.

To better stay connected with the Hyperledger developers, it is recommended that you create a Linux Foundation ID at https://identity.linuxfoundation.org.  With the Linux Foundation ID you can access our RocketChat server (like Slack) at https://chat.hyperledger.org.  We also have active mailing lists that you can join by going to https://lists.hyperledger.org/mailman/listinfo.  You will also be able to access our JIRA bug tracking system at https://jira.hyperledger.org.

Thank you for your consideration.  We hope that you will come join us in making solid blockchain technologies and platforms for the benefit of many different industries/applications.

# Dos
* Follow [HackerOne’s disclosure guidelines](https://www.hackerone.com/disclosure-guidelines).
* Provide detailed reports with reproducible steps.  If there is insufficient detail and we cannot reproduce the issue, the issue will not be eligible for a reward.
* Submit one vulnerability per report, unless you can chain the vulnerabilities.
* Treat everybody with [respect](https://wiki.hyperledger.org/community/hyperledger-project-code-of-conduct#respect), professionalism, fairness, and sensitivity to our many differences and strengths, including in situations of high pressure and urgency.
* Be familiar with and follow our [community code of conduct](https://wiki.hyperledger.org/community/hyperledger-project-code-of-conduct).
Come hang out with us--or just lurk--in our chat and mailing lists.  We’d love to meet you and have you join our community.

# Don’ts
* Social engineering of any kind (e.g. phishing, vishing, smishing).  That is strictly prohibited and outside of the scope of this bounty program.

# Program Rules
* When duplicate reports occur, we will only award the first report received--provided that the report is well formed, can be fully reproduced, and meets all other submission criteria.
* Multiple vulnerabilities caused by one underlying issue will be awarded one bounty.
* Amounts below are the minimum we will pay per category. We aim to be fair; all reward amounts are at our discretion.

#Rewards
Our rewards are based on the impact of a vulnerability. Please note these are general guidelines and examples, and that reward decisions are up to the discretion of the Hyperledger Foundation security team. 

## Critical severity bugs - minimum [$2000]
Types of impacts that Hyperledger would consider to be critical include:
* Fabric Certificate Authority bypasses--all endorsers and authentication of who can and cannot create transactions that go into the blockchain rely on the Fabric CA.
* Preventing consensus--figuring out a way to stop the distributed system from achieving consensus. * Fabric uses a pluggable architecture for distributed consensus. Issues that can prevent consensus would be considered critical.
* Escaping from a chaincode container--breaking out of the VM.
* Unauthorized modifications of chaincode--changing the code that is executed inside of the VM. 
Types of vulnerabilities that may result in these impacts include:
* Vertical authentication bypass.
* Recording unauthorized, invalid, or forged transactions in the blockchain.
* Amplification attack where chaincode generates malicious network traffic.
* Denial of service of the whole blockchain by stopping chaincode execution and/or the consensus network.
* Establishing a persistent beachhead inside of the firewall protecting the Fabric network.

## High severity bugs - minimum [$1500]
Types of impacts that Hyperledger would consider to be high include:
* Confused deputy attack on the Fabric Certificate Authority--mistakenly issued credentials to access the permissioned network or being re-issued another user’s credentials or otherwise affecting the permissions of other users. 
* Taking down any Fabric component (e.g. endorser, ordering service, membership service, consensus network) through malformed data submitted from the outside via the API.
Types of vulnerabilities that may result in these impacts include:
* Lateral authentication bypass.
* Remote denial of service.
* Default configuration errors.

## Medium severity bugs - minimum [$500]: 
Types of impacts that Hyperledger would consider to be medium include:
* Taking down any Fabric component (e.g. endorser, ordering service, membership service, consensus network) through malformed data and/or fuzzing of its API used for inter-service communication behind the firewall.  If you fuzz from a privileged network position (e.g. behind the firewall), then the vulnerability is of medium severity unless you can show that it can also be triggered from an unprivileged network position.
Types of vulnerabilities that may result in these impacts include:
* General instability.

## Low severity bugs - minimum [$200]:
Types of impacts that Hyperledger would consider to be low include:
* Vulnerabilities found in demo/example configuration, chaincode, and applications.
Types of vulnerabilities that may result in these impacts include:
* Footgun attack.

# Scope
* Only those projects listed, and the identified repositories are in scope.
* Issues that may impact users with runtime components in production environments.
If you have any questions, please ask us at security@hyperledger.org BEFORE performing any testing.

## Out of Scope
* All of the Linux Foundation infrastructure in general and all of the Hyperledger Foundation infrastructure, specifically.
* Any Hyperledger projects that have not reached 1.0 status. Only issues found against Hyperledger Fabric 1.0+ will be eligible for bounties.
* All test and documentation code.
* Issues in non-Hyperledger dependent projects. Issues in dependent projects should be reported directly to the respective project. Hyperledger projects regularly update dependency versions to fix issues identified in dependent projects.
If you identify any scopes not listed above that you believe belong to Hyperledger, please let us know at security@hyperledger.org BEFORE performing any testing.

## Out of scope vulnerabilities
When reporting vulnerabilities, please consider (1) attack scenario / exploitability, and (2) security impact of the bug. The following issues are considered out of scope:
* Intentionally malicious chaincode.  Chaincode is Go running in a docker container.  The security anchors in the controlled chaincode provisioning system that is designed to carefully manage what chaincode is installed and available to run.
* Denial of service of any component (e.g. Endorser, etc) from a privileged network position (i.e. inside the firewall).  Fabric is designed to run all components behind a corporate firewall.  Clients outside the firewall will talk to a network service that uses the API to talk to the rest of the system behind the firewall.
* Insecure configurations.  We do our best to prevent the possibility of insecure configuration but we don’t see this as being in scope.  If you find something, it would be great if you just filed a bug in our JIRA.
* Documentation errors.  We strive to keep the documentation up to date, but sometimes it becomes stale.  We do not consider this to be in scope however we encourage you to file a JIRA bug or a pull request to fix it.

Thank you for helping keep Hyperledger and our users safe!

# Getting Started
To help you get started with Hyperledger Fabric we have a few pieces of documentation:
* [The official Hyperledger Fabric documentation](http://hyperledger-fabric.readthedocs.io/en/latest/)
* We have also developed an introductory online course for Hyperledger Fabric, Sawtooth, and Iroha. It contains instructions for setting up a network and building an application on Hyperledger Fabric. The course is here: 
https://courses.edx.org/courses/course-v1:LinuxFoundationX+LFS171x+3T2017/course/

We also have a Hyperledger calendar of events where we will list community [hackathons/hackfests](https://www.hyperledger.org/events) where you can meet more Hyperledger developers and get more involved in our community.
