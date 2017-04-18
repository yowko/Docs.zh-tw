---
title: "BinaryMessageEncodingBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# BinaryMessageEncodingBindingElement
BinaryMessageEncodingBindingElement  
  
## 語法  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## 方法  
 BinaryMessageEncodingBindingElement 類別並未定義任何方法。  
  
## 屬性  
 BinaryMessageEncodingBindingElement 類別具有下列屬性。  
  
## MaxReadPoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時讀取之訊息數目 \(在不配置新讀取器的情況下\) 的整數。  
  
## MaxSessionSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 此值可指定用於編碼的緩衝區大小 \(以位元組為單位\)。  
  
## MaxWritePoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時傳送之訊息數目 \(在不配置新寫入器的情況下\) 的整數。  
  
## ReaderQuotas  
 資料型別：XmlDictionaryReaderQuotas  
  
 存取類型：唯讀  
  
 讀取器的配額。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>