---
title: "HttpsTransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e78aa8c6-b53b-4105-a900-d3e7a39670f2
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# HttpsTransportBindingElement
HttpsTransportBindingElement  
  
## 語法  
  
```  
class HttpsTransportBindingElement : HttpTransportBindingElement  
{  
  boolean RequireClientCertificate;  
};  
```  
  
## 方法  
 HttpsTransportBindingElement 類別並未定義任何方法。  
  
## 屬性  
 HttpsTransportBindingElement 類別具有下列屬性：  
  
### RequireClientCertificate  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 一個值，這個值會指出是否需要 SSL 用戶端驗證。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>