---
title: "SecurityBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# SecurityBindingElement
SecurityBindingElement  
  
## 語法  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## 方法  
 SecurityBindingElement 類別不會定義任何方法。  
  
## 屬性  
 SecurityBindingElement 類別具有下列屬性：  
  
### DefaultAlgorithmSuite  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定要與繫結一起使用的演算法。  
  
### IncludeTimestamp  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 布林值，這個值會指定每個訊息是否包含時間戳記。  
  
### KeyEntropyMode  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於建立金鑰的 Entropy 來源。  
  
### LocalServiceSecuritySettings  
 資料型別：LocalServiceSecuritySettings  
  
 存取類型：唯讀  
  
 用於本機服務的繫結特定安全性屬性。  
  
### MessageSecurityVersion  
 資料型別：字串  
  
 存取類型：唯讀  
  
 用於訊息安全性的版本。  
  
### SecurityHeaderLayout  
 資料型別：字串  
  
 存取類型：唯讀  
  
 此繫結之安全性標頭中的項目順序。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>