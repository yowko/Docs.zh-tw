---
title: "System.ServiceModel.Channels.TcpConnectError | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 22d93797-072e-405d-a3e0-5c519ddf290b
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# System.ServiceModel.Channels.TcpConnectError
TCP 連線作業失敗。  
  
## 描述  
 這個警告層級追蹤表示無法連接到 TCP 端點。如果位於指定之 IP 位址和連接埠的遠端端點沒有回應，就會發生這個問題。如果後續對其他有效 IP 位址 \(例如 IPv4 或 IPv6 位址，或其他代表指定主機名稱的 IP 位址\) 的連線嘗試成功的話，則會忽略這個追蹤。這個追內的例外狀況會顯示有關錯誤的其他資訊。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)