---
title: "應用程式開發中的 PNRP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# 應用程式開發中的 PNRP
在 Windows Vista 中， Web 應用程式可以將一個簡單的 PNRP Application Programming Interfaces \(API\) 存取發行物名稱和解析函式。  
  
## 實作一個對等名稱解析通訊協定  
 使用簡化的 API， PNRP Cloud 未明確指定登錄姓名和地址，PNRP 元件會自動決定適當的 Cloud 聯結和位址發行至 Cloud。  
  
 對於在 Windows Vista 上的高度簡化的 PNRP 名稱解析， PNRP 名稱出現在整合式 getaddrinfo\(\) Windows Sockets 函式。  若要使用 PNRP 名稱解析成 IPv6 位址，應用程式可以使用 getaddrinfo\(\) 函式會解析為完整網域名稱 name.prnp \(FQDN\)。  網站，名稱為解析的對等名稱。  pnrp。  網路網域是在 Windows Vista 上保留的 PNRP 網域名稱轉換成的。  
  
 藉由在點對點應用程式之間的訊息是由基礎結構仍在處理 \(例如 PeerChannel 和 WCF [大型資料和資料流](http://go.microsoft.com/fwlink/?LinkID=179652)。  
  
## 請參閱  
 <xref:System.Net.PeerToPeer>