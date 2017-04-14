---
title: "39458 - TrackingRecordTruncated | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 39458 - TrackingRecordTruncated
## 屬性  
  
|||  
|-|-|  
|ID|39458|  
|關鍵字|WFTracking|  
|層級|警告|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Debug|  
  
## 描述  
 表示追蹤記錄已被截斷。  變數\/標註\/使用者資料已移除。  
  
## 訊息  
 已將截斷的追蹤記錄 %1 寫入提供者 %2 的 ETW 工作階段。  變數\/附註\/使用者資料已移除  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|RecordNumber|xs:string|追蹤記錄號碼。|  
|ProviderId|xs:string|ETW 提供者 ID。|  
|AppDomain|xs:string|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|