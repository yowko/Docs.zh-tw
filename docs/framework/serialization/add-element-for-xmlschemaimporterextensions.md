---
title: "&lt;xmlSchemaImporterExtensions&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
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
  - "<xmlSchemaImporterExtensions> 項目的 <add> 項目"
  - "XML 序列化, 組態"
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;xmlSchemaImporterExtensions&gt; 的 &lt;add&gt; 項目
加入 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別，將 XSD 型別對應至 .NET Framework 型別。  如需有關組態檔的詳細資訊，請參閱 [組態檔結構描述](../../../docs/framework/configure-apps/file-schema/index.md)。  
  
 \<XmlSchemaImporterExtensions\>  
\<add\>  
  
## 語法  
  
```  
  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**name**|用來尋找執行個體的簡單名稱。|  
|**type**|必要項。  指定要加入的結構描述擴充功能類別。  **type** 屬性值必須在單行，且包括完整型別名稱。  當組件置於全域組件快取 \(GAC\) 中時，也必須包含簽署組件的版本、文化特性和公開金鑰語彙基元。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|\<xmlSchemaImporterExtensions\>|包含 <xref:System.Xml.Serialization.XmlSchemaImporter> 使用的型別。|  
  
## 範例  
 下列程式碼範例會加入 XmlSchemaImporter 在對應型別時可使用的副檔名類型。  
  
```  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 [\<system.xml.serialization\> 項目](../../../docs/framework/serialization/system-xml-serialization-element.md)   
 [\<schemaImporterExtensions\> 項目](../../../docs/framework/serialization/schemaimporterextensions-element.md)