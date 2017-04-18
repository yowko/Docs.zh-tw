---
title: "ActivityTransfer | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ActivityTransfer
活動傳輸事件  
  
## 語法  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## 方法  
 ActivityTransfer 類別並未定義任何方法。  
  
## 屬性  
 ActivityTransfer 類別具有下列屬性：  
  
### ActivityID  
  
-   資料型別：物件                   
     存取類型：唯讀  
  
-   活動識別碼  
  
### RelatedActivityID  
  
-   資料型別：物件                   
     存取類型：唯讀  
  
-   相關活動識別碼  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義。|