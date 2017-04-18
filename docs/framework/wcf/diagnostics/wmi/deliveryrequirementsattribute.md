---
title: "DeliveryRequirementsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## 語法  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## 方法  
 DeliveryRequirementsAttribute 類別不會定義任何方法。  
  
## 屬性  
 DeliveryRequirementsAttribute 類別具有下列屬性：  
  
### QueuedDeliveryRequirements  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定服務的繫結是否支援合約。  
  
### RequireOrderedDelivery  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定繫結是否支援已排序的訊息。  
  
### TargetContract  
 資料型別：字串  
  
 存取類型：唯讀  
  
 它所套用的合約。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>