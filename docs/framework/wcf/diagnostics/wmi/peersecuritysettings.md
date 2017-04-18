---
title: "PeerSecuritySettings | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# PeerSecuritySettings
PeerSecuritySettings  
  
## 語法  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## 方法  
 PeerSecuritySettings 類別並未定義任何方法。  
  
## 屬性  
 PeerSecuritySettings 類別有下列屬性：  
  
### 模式  
 資料型別：字串  
  
 存取類型：唯讀  
  
 使用繫結設定之端點是否採用訊息層級與傳輸層級安全性。  
  
### 傳輸  
 資料型別：PeerTransportSecuritySettings  
  
 存取類型：唯讀  
  
 傳輸安全性設定。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.PeerSecuritySettings>