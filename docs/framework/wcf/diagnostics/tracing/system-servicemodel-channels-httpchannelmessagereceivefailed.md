---
title: "System.ServiceModel.Channels.HttpChannelMessageReceiveFailed | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
無法透過 HTTP 通道接收訊息。  
  
## 描述  
 這個追蹤可以發出做為警告或錯誤。在這兩種情況下，當找不到與傳入 HTTP 要求相容的接聽項，並且 HTTP 要求已捨棄時，就會發出追蹤。之所以發生，是因為沒有任何 HTTP 接聽項辨識出要求的 HTTP 動詞，或者在要求的目標位址上沒有任何接聽項在接聽。在自我裝載的案例中，會發出追蹤做為警告，而當服務裝載在 IIS 時，則會發出追蹤做為錯誤。  
  
## 請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)   
 [使用追蹤來疑難排解應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)   
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)