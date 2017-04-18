---
title: "TraceListener | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c2c0b595-a384-4eb3-b94d-1b3be7cc7a5c
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# TraceListener
TraceListener。  
  
## 語法  
  
```  
class TraceListener  
{  
  string Name;  
  TraceListenerArgument TraceListenerArguments[];  
};  
```  
  
## 方法  
 TraceListener 類別沒有定義任何方法。  
  
## 屬性  
 TraceListener 類別有下列屬性：  
  
### 名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 追蹤接聽項的名稱。  
  
### TraceListenerArguments  
 資料型別：TraceListenerArgument 陣列  
  
 存取類型：唯讀  
  
 追蹤接聽項的引數。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|