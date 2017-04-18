---
title: "PrivacyNoticeBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## 語法  
  
```  
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## 方法  
 PrivacyNoticeBindingElement 類別並未定義任何方法。  
  
## 屬性  
 PrivacyNoticeBindingElement 類別具有下列屬性：  
  
### PrivacyNoticeVersion  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 隱私權注意事項的版本。  
  
### URL  
 資料型別：字串  
  
 存取類型：唯讀  
  
 隱私權注意事項所在的 URL。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>