---
title: "ServiceThrottlingBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## 語法  
  
```  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## 方法  
 ServiceThrottlingBehavior 類別不會定義任何方法。  
  
## 屬性  
 ServiceThrottlingBehavior 類別具有下列屬性：  
  
### MaxConcurrentCalls  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 在 ServiceHost 中的所有發送器物件上主動處理的訊息數目上限。  
  
### MaxConcurrentInstances  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 一次可執行的服務物件數目上限。  
  
### MaxConcurrentSessions  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 主機一次可接受的工作階段數目上限。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>