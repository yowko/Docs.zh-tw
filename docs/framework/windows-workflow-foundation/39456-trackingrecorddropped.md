---
title: "39456 - TrackingRecordDropped | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39456 - TrackingRecordDropped
## 屬性  
  
|||  
|-|-|  
|ID|39456|  
|關鍵字|WFTracking|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示追蹤記錄的大小已超出 ETW 工作階段提供者所允許的最大值而丟棄追蹤記錄。  
  
## 訊息  
 追蹤記錄 %1 的大小已超出提供者 %2 的 ETW 工作階段所允許的最大值  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|例外狀況|xs:string|例外狀況的例外狀況詳細資料|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|