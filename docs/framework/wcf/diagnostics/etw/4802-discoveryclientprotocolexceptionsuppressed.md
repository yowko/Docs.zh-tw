---
title: "4802 - DiscoveryClientProtocolExceptionSuppressed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 568212f7-1060-4f5c-a7a0-1352c7cc743b
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 4802 - DiscoveryClientProtocolExceptionSuppressed
## 屬性  
  
|||  
|-|-|  
|ID|4802|  
|關鍵字|探索|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 如果 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的，就會發出此事件。  
  
## 訊息  
 ProtocolException 在關閉 DiscoveryClient 的同時是隱藏的。  這可能是因為 DiscoveryService 仍在嘗試傳送回應給 DiscoveryClient。  
  
## 詳細資料