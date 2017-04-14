---
title: "WCF 及 WebSockets | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF 及 WebSockets
.NET Framework 4.5 在 Windows Communication Foundation 中引入了 WebSockets 的支援。WebSockets 是基於標準的高效率技術，可在標準 HTTP 通訊埠 80 和 443 上進行雙向通訊。使用標準 HTTP 通訊埠允許 WebSockets 透過媒介在 Web 上進行通訊。為了支援透過 WebSocket 傳輸所進行通訊，已加入兩個新的標準繫結。<xref:System.ServiceModel.NetHttpBinding> 和 <xref:System.ServiceModel.NetHttpsBinding>。藉由存取 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> 屬性，即可在 <xref:> System.ServiceModel.Channels.HttpTransportBinding?qualifyHint=False&autoUpgrade=True 項目上設定 WebSockets 的特定設定。  
  
## 在本節中  
 [使用 NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 討論 <xref:System.ServiceModel.NetHttpBinding> 及其設定方式。  
  
 [HOW TO：建立會透過 WebSockets 進行通訊的 WCF 服務。](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 說明如何建立透過 WebSockets 進行通訊的 WCF 服務。  
  
## 參考  
  
## 相關章節