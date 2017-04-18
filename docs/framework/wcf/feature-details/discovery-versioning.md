---
title: "探索版本控制 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f91c6d0a-3af2-45c5-9a5c-e75390619836
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 探索版本控制
本主題簡要概述部分新探索功能的實作，  同時也概要說明如何選取要使用的探索版本。  
  
## 探索版本控制  
 探索功能包括支援三種版本的 WS\_Discovery 通訊協定。  探索 API 可讓您選取要使用的通訊協定版本。  本文件簡要描述與版本控制相關的設定。  
  
 下列探索類別現在具有 <xref:System.ServiceModel.Discovery.DiscoveryVersion> 屬性，並且會在其建構函式中採用 <xref:System.ServiceModel.Discovery.DiscoveryVersion> 引數：  
  
-   <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>  
  
-   <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>  
  
### DiscoveryVersion.WSDiscoveryApril2005  
 若提供 <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryApril2005> 做為建構函式參數，會使實作使用 April2005 版的 WS\-Discovery 通訊協定。  這個版本對應至所發行的 WS\-Discovery 通訊協定規格版本。  請使用這個版本與採用 April2005 版 WS\-Discovery 的舊版應用程式交互操作。  
  
### DiscoveryVersion.WSDiscovery11  
 API 所使用的預設探索版本是  <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscovery11>。  這是最新的標準版 WS\-Discovery 通訊協定。  
  
## DiscoveryVersion.WSDiscoveryCD1  
 若提供 <xref:System.ServiceModel.Discovery.DiscoveryVersion.WSDiscoveryCD1> 做為建構函式參數，會使實作使用 WS\-Discovery 通訊協定的 Committee Draft 1 版。  請使用這個版本的通訊協定與執行 CD1 版 WS\-Discovery 的實作交互操作。  
  
## 支援在單一服務主機上進行不同探索版本的多個 UDP 探索端點  
 您可以在單一服務主機上公開多個不同探索版本的 UDP 探索端點。  若要這麼做，您必須為每個 UDP 探索端點指定一個唯一位址。  下列範例顯示如何執行這項工作。  
  
```  
UdpDiscoveryEndpoint newVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscovery11);  
UdpDiscoveryEndpoint oldVersionUdpEndpoint = new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
  
newVersionUdpEndpoint.Address = new EndpointAddress(newVersionUdpEndpoint.Address.Uri.ToString() + "/version11");  
oldVersionUdpEndpoint.Address = new EndpointAddress(oldVersionUdpEndpoint.Address.Uri.ToString() + "/versionAril2005");  
  
serviceHost.AddServiceEndpoint(newVersionUdpEndpoint);  
serviceHost.AddServiceEndpoint(oldVersionUdpEndpoint);  
  
```