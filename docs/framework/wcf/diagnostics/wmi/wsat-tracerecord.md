---
title: "WSAT_TraceRecord | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# WSAT_TraceRecord
WSAT\_TraceRecord  
  
## 語法  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## 方法  
 WSAT\_TraceRecord 類別並未定義任何方法。  
  
## 屬性  
 WSAT\_TraceRecord 類別有下列屬性：  
  
### ActivityID  
 資料型別：物件  
存取類型：唯讀  
  
 追蹤記錄的活動識別碼。  
  
### EventID  
 資料型別：sint32  
存取類型：唯讀  
  
 追蹤記錄的事件識別碼。  
  
### TraceRecord  
 資料型別：字串  
存取類型：唯讀  
  
 追蹤記錄  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|