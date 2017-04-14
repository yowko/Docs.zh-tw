---
title: "TransportBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransportBindingElement
TransportBindingElement  
  
## 語法  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## 方法  
 TransportBindingElement 類別並未定義任何方法。  
  
## 屬性  
 TransportBindingElement 類別具有下列屬性：  
  
### ManualAddressing  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 指定使用者是否要取得訊息定址控制權的布林值。  
  
### MaxBufferPoolSize  
 資料型別：sint64  
  
 存取類型：唯讀  
  
 繫結的緩衝集區大小上限。  
  
### MaxReceivedMessageSize  
 資料型別：sint64  
  
 存取類型：唯讀  
  
 此繫結所處理之訊息的大小上限。  
  
### Scheme  
 資料型別：字串  
  
 存取類型：唯讀  
  
 傳輸的 URI 配置。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.TransportBindingElement>