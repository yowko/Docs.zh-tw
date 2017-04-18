---
title: "&lt;dateTimeSerialization&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<dateTimeSerialization> 項目"
  - "dateTimeSerialization 項目"
  - "XML 序列化, 設定"
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;dateTimeSerialization&gt; 項目
判斷 <xref:System.DateTime> 物件的序列化模式。  
  
## 語法  
  
```  
  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`mode`|選擇項。  指定序列化模式。  設定為其中一個 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 值。  預設為 **RoundTrip**。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|system.xml.serialization|用來控制 XML 序列化的最上層項目。|  
  
## 備註  
 在 .NET Framework 的 1.0、1.1 和 2.0 版以及更新版本中，將這個屬性設為 **Local** 時，<xref:System.DateTime> 物件一定會格式化為本地時間。  也就是說，本地時區資訊一定會包含在序列化資料中。  將這個屬性設為 **Local**，確保與舊版 .NET Framework 的相容性。  
  
 在將此屬性設為 **Roundtrip** 的 .NET Framework 2.0 版及更新版本中，會檢查 <xref:System.DateTime> 物件以判斷其位於本地、UTC 或非特定時區。  然後 <xref:System.DateTime> 物件會以保留此資訊的方式序列化。  這是預設行為，並建議所有新的應用程式不要與舊版 Framework 進行通訊。  
  
## 請參閱  
 <xref:System.DateTime>   
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<schemaImporterExtensions\> 項目](../../../docs/framework/serialization/schemaimporterextensions-element.md)   
 [\<xmlSchemaImporterExtensions\> 的 \<add\> 項目](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)