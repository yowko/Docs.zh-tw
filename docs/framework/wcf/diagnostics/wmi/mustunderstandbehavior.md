---
title: "MustUnderstandBehavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# MustUnderstandBehavior
MustUnderstandBehavior  
  
## 語法  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## 方法  
 MustUnderstandBehavior 類別並未定義任何方法。  
  
## 屬性  
 MustUnderstandBehavior 類別具有下列屬性：  
  
### ValidateMustUnderstand  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 當 `true` 時，所有具有 `MustUnderstand` 屬性且未處理的 SOAP 標頭，會導致該行為擲出例外狀況。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>