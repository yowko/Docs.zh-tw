---
title: "&lt;schemaImporterExtensions&gt; 項目 | Microsoft Docs"
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
  - "<schemaImporterExtensions> 項目"
  - "schemaImporterExtensions 項目"
  - "XML 序列化, 設定"
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;schemaImporterExtensions&gt; 項目
包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 用來對應 XSD 型別至 .NET Framework 型別的型別。  如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。  
  
## 語法  
  
```  
  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<xmlSchemaImporterExtensions\> 的 \<add\> 項目](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)|加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別以建立對應。|  
  
## 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)|用來控制 XML 序列化的最上層項目。|  
  
## 範例  
 下列程式碼範例描述如何加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 在對應 XSD 型別至 .NET Framework 型別時使用的型別。  
  
```  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## 請參閱  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<dateTimeSerialization\> 項目](../../../docs/framework/serialization/datetimeserialization-element.md)   
 [\<xmlSchemaImporterExtensions\> 的 \<add\> 項目](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)