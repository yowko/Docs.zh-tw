---
title: "TextMessageEncodingBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TextMessageEncodingBindingElement
TextMessageEncodingBindingElement  
  
## 語法  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## 方法  
 TextMessageEncodingBindingElement 類別不會定義任何方法。  
  
## 屬性  
 TextMessageEncodingBindingElement 類別具有下列屬性：  
  
### Encoding  
 資料型別：字串  
  
 存取類型：唯讀  
  
 要在繫結上發出訊息時使用的字元集編碼方式。  
  
### MaxReadPoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時讀取之訊息數目 \(在不配置新讀取器的情況下\) 的整數。  
  
### MaxWritePoolSize  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 定義可同時傳送之訊息數目 \(在不配置新寫入器的情況下\) 的整數。  
  
### ReaderQuotas  
 資料型別：XmlDictionaryReaderQuotas  
  
 存取類型：唯讀  
  
 讀取器的配額。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>