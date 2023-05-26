---
title: "Machine Learning for Android Malware Detection Using Permission and API Calls"
collection: publications
permalink: /publication/ICTAI2010
date: 2013-04-11
venue: 'ICTAI'
citation: Naser Peiravian, Xingquan Zhu. ICTAI (2013)
---
[[PDF]](https://ieeexplore.ieee.org/abstract/document/6735264)

## Abstract
The Google Android mobile phone platform is one of the most anticipated smartphone operating systems on the market. The open source Android platform allows developers to take full advantage of the mobile operation system, but also raises significant issues related to malicious applications. On one hand, the popularity of Android absorbs attention of most developers for producing their applications on this platform. The increased numbers of applications, on the other hand, prepares a suitable prone for some users to develop different kinds of malware and insert them in Google Android market or other third party markets as safe applications. In this paper, we propose to combine permission and API (Application Program Interface) calls and use machine learning methods to detect malicious Android Apps. In our design, the permission is extracted from each App's profile information and the APIs are extracted from the packed App file by using packages and classes to represent API calls. By using permissions and API calls as features to characterize each Apps, we can learn a classifier to identify whether an App is potentially malicious or not. An inherent advantage of our method is that it does not need to involve any dynamical tracing of the system calls but only uses simple static analysis to find system functions involved in each App. In addition, because permission settings and APIs are alwaysavailable for each App, our method can be generalized to all mobile applications. Experiments on real-world Apps with more than 1200 malware and 1200 benign samples validate the algorithm performance.
