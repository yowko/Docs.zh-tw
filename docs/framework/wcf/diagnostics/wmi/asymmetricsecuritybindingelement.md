---
title: "AsymmetricSecurityBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# AsymmetricSecurityBindingElement
AsymmetricSecurityBindingElement  
  
## 語法  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## 方法  
 AsymmetricSecurityBindingElement 類別不會定義任何方法。  
  
## 屬性  
 AsymmetricSecurityBindingElement 類別具有下列屬性：  
  
### MessageProtectionOrder  
 資料型別：字串  
  
 存取類型：唯讀  
  
 這個繫結的訊息加密和簽章順序。  
  
### RequireSignatureConfirmation  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 繫結是否需要簽章確認。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>