---
title: "ServiceTimeoutsBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## 語法  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## 方法  
 ServiceTimeoutsBehavior 類別不會定義任何方法。  
  
## 屬性  
 ServiceTimeoutsBehavior 類別具有下列屬性：  
  
### TransactionTimeout  
 資料型別：日期時間  
  
 存取類型：唯讀  
  
 交易必須完成的期間。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>