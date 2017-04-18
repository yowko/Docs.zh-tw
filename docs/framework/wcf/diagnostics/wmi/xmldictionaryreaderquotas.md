---
title: "XmlDictionaryReaderQuotas | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## 語法  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## 方法  
 XmlDictionaryReaderQuotas 類別不會定義任何方法。  
  
## 屬性  
 XmlDictionaryReaderQuotas 類別有下列屬性：  
  
### MaxArrayLength  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 允許的陣列長度上限。  
  
### MaxBytesPerRead  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 允許每個讀取動作傳回的位元組上限。  
  
### MaxDepth  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 每個讀取動作的巢狀節點深度上限。  
  
### MaxNameTableCharCount  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 資料表名稱允許的字元數目上限。  
  
### MaxStringContentLength  
 資料型別：sint32  
  
 存取類型：唯讀  
  
 XML 項目內容允許的字元數目上限。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.Xml.XmlDictionaryReaderQuotas>   
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>