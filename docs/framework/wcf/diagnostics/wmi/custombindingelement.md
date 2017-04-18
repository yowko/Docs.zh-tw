---
title: "CustomBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df959dc5-1aef-4338-a123-6ff3e7bc37af
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# CustomBindingElement
CustomBindingElement  
  
## 語法  
  
```  
class CustomBindingElement : BindingElement  
{  
  string Name;  
};  
```  
  
## 方法  
 CustomBindingElement 類別不會定義任何方法。  
  
## 屬性  
 CustomBindingElement 類別具有下列屬性：  
  
### 名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 包含繫結之組態名稱的字串。  這個值是使用者定義的字串，它會充當自訂繫結的識別字串。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.CustomBinding>