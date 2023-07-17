<div id="top"></div>

<div align="center">

# CakeSystem

<h2>A mine pool level operation and maintenance tools👍 </h2>

<img src="/image/logo.png" alt="Logo" width="170">

[![CakeSystem][CakeSystem.io-badge]][CakeSystem.io]
[![Downloads][downloads-badge]][releases]
[![Stargazers][stars-shield]][stars-url]

<a href="https://github.com/CakeSystem/CakeSystem/blob/main/README.md">简体中文</a>｜<a href="https://github.com/CakeSystem/CakeSystem/blob/main/i18n/zh_cn.md">English</a>


(Partial Preview)

<img src="/image/1.png" alt="Logo" width="670">
   <img src="/image/2.png" alt="Logo" width="670">
      <img src="/image/3.png" alt="Logo" width="670">

</div>

# Join the discussion group

Telegram：<a href="https://t.me/+OiG7xOS-ZZg1ZDI1">https://t.me/+OiG7xOS-ZZg1ZDI1</a>

<!-- Discord：<a href="sadfasfdasfsa">sadfasfdasfsa</a> -->

# Special thanks

<img src="/image/icon-logo-blue.png" alt="Logo" width="100">

<img src="/image/poolin.svg" alt="Logo" width="100">

<p>Thanks for the technical support provided by the mine pool😊</p>

# Supported algorithms

For the supported algorithm, the corresponding currency will be updated without heat at any time, and the client 0 will bear the burden


| arithmetic      | Support     | Relevant currency |
| --------------- | ------------| ------------------|
| SHA256          | ✅          | BTC、BCH...        
| ETHASH          | ✅          | ETC、ETHW、ETHF、ETC+ZIL、ETHW+ZIL、ETHF+ZIL
| SCRYPT          | ✅          | LTC...
| KHEAVYHASH      | ✅          | KASPA...


# Service Agreement



[CakeSystem.io]: https://github.com/CakeSystem/CakeSystem
[CakeSystem.io-badge]: https://img.shields.io/badge/CakeSystem-v0.0.1-green?logo=rust
[downloads-badge]: https://img.shields.io/github/downloads/ajeetdsouza/zoxide/total?logo=github&logoColor=white&style=flat-square
[releases]: https://github.com/CakeSystem/CakeSystem/releases
[stars-url]: https://github.com/CakeSystem/CakeSystem/stargazers
[stars-shield]: https://img.shields.io/github/stars/CakeSystem/CakeSystem.svg?style=flat
[stars-url]: https://github.com/CakeSystem/CakeSystem/stargazers

# Installation 

1. **Install**

   Select your applicable operating system

   <details open>
   <summary>Linux</summary>

   > Run the following shell instructions to run the toolkit
   >
   > ```sh
   >  bash <(curl -s -L https://github.com/CakeSystem/CakeSystem/raw/main/install.sh)
   > ```
   >
   > After running successfully, you will see the following menu.
   >

   </details>

   <details open>
   <summary>Windows</summary>

   > Please download the specified version directly from the Windows directory of this project:
   >
   > ```sh
   > https://github.com/CakeSystem/CakeSystem/tree/main/windows
   > ```
   >

   </details>


# Version Log
```
2.0.6
Optimized power compensation, the power compensation option is now hidden, and power is allocated to all miners by default 
 
Optimized E9pro, now all mining pools can run full E9pro, and the calculation of e9pro in rust is accurate and consistent with the mining pool 
 
Added a pumping mode 
 
Added a mode for connecting mine pools 
 
Optimized mining machine with high computing power


2.0.5

[Important Update] Fixed a bug where RUST was suspended in windows 
 
Fixed high inefficiency of kas Glacier and other chip machines 
 
Compatible with the etc gtv66 chip, improve the etc computing power calculation 
 
Fixed some bugs in power statistics

2.0.4 
The default mode of computing power compensation is optimized to further reduce inefficiency 
 
Optimized the performance of kaspa under different mining pool protocols, lolminer and gminer now work in all mining pools 
 
Optimized the calculation logic of the etc related algorithm, and now the calculation and pumping are more accurate 
 
The underlying optimization improves the hardware utilization 
 
Optimized share display bug 
 
Optimize the home active distribution list

2.0.3
Fixed a serious BUG caused by disconnection reconnection mechanism

2.0.2
Fixed a software crash caused by concurrency  
Statistical optimization of computing powe

2.0.0 
Multiple client details optimization 
 
Now the pumping accuracy is MAX 
 
Added power compensation configuration, now the loss of power compensation can be configured on the port 
 
The mechanism of re-connection of broken lines is added to ensure that the mining machine with frequent disconnection can also pump normally 
 
Fixed kas high invalidation bug 
 
The underlying algorithm engine was updated and reconstructed, and began to rapidly support small coins 
 
Added SC currency 
 
Added CFX currency 
 
Fixed an issue where LTC was highly ineffective in viabtc 
 
Fixed an issue with inaccurate LTC power display 
 
Fixed LTC computing power loss problem 
 
Remove the limit on the number of pumping wallets 
 
Lifting cross-pond pumping restrictions 
 
Optimized port logs, added program runtime logs, and enabled device logs

The low-level optimization avoids several bugs that are easy to cause program crashes

1.0.4
Optimized the efficiency of some BTC models, optimized the rejection rate of viabtc and ant mine pool
optimized a detail bug, and further reduced the inefficiency

1.0.3
Performance optimization 
Added configuration import and export in json, kt, and excel formats
   
1.0.2
The underlying reconstruction optimizes the processing and statistics of multiple links 
It is deeply optimized for e9pro 
Open error log
   
1.0.1
Fixed a bug caused by links
   
1.0.0
Open test
   
0.9.999
A serious security breach was fixed
Optimized commission logic for all currencies
   
0.9.99
Optimize BTC, LTC
Optimized mean delay display is not accurate
   
0.9.98
Optimize the bottom layer and reduce losses
   
0.0.97
Fixed a serious bug in program pseudo death
   
0.0.96
The perfect BTC@KAS
   
0.0.95
   
fix...

0.0.94
fix...
   
0.9.93
fix
   
0.0.92
Fixed a bug where the hot update wallet would cause the application to crash. Fixed some kernel kas connection issues 
 
Fixed ltc small power display bug
   
0.0.91
Fixed a bug where the hot update wallet caused the program to crash

Fixed kas not working properly due to changes in the previous version

0.9.9
Optimized a lot of details

Optimized Yami equipment

Further reducing the probability of ineffectiveness (although already very low)

Optimized memory and CPU usage

0.1.4
Optimize e9 and e9pro
   
0.1.3
Optimizing Antminer s17

0.1.2
Fixed a serious issue of task chaos for multiple devices under Rust

Fixed issue where kas was unable to receive tasks

0.1.0
Release of internal test version
```
