---
title: "402 - StartSignpostEvent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 402 - StartSignpostEvent
## 屬性  
  
|||  
|-|-|  
|ID|402|  
|關鍵字|疑難排解|  
|層級|資訊|  
|通道|Microsoft\-Windows\-Application Server\-Applications\/Analytic|  
  
## 描述  
 此活動會標記端對端活動的開始。其中包含了活動的名稱。  
  
## 訊息  
 活動界限。  
  
## 詳細資料  
  
|資料項目名稱|資料項目型別|描述|  
|------------|------------|--------|  
|延伸資料|`xs:string`|活動名稱。|  
|AppDomain|`xs:string`|由 AppDomain.CurrentDomain.FriendlyName 傳回的字串。|