---
title: "AspNetCompatibilityRequirementsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00908a39-a21b-4029-bbb9-33e5a6ed25a7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# AspNetCompatibilityRequirementsAttribute
AspNetCompatibilityRequirementsAttribute  
  
## 語法  
  
```  
class AspNetCompatibilityRequirementsAttribute : Behavior  
{  
  string RequirementsMode;  
};  
```  
  
## 方法  
 AspNetCompatibilityRequirementsAttribute 類別並未定義任何方法。  
  
## 屬性  
 AspNetCompatibilityRequirementsAttribute 類別具有下列屬性。  
  
### RequirementsMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 代表 Asp.Net 相容模式是否作用中。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceHostingEnvironment.AspNetCompatibilityEnabled%2A>