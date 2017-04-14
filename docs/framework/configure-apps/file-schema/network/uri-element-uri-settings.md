---
title: "&lt;Uri&gt; 項目 (Uri 設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;Uri&gt; 項目 (Uri 設定)
內含設定，指定 .NET Framework 如何處理使用統一資源識別元 \(URI\) 表示的網址。  
  
## 結構描述階層架構  
 [\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<uri\>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## 語法  
  
```  
<uri>  
</uri>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[idn](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|指定是否要對網域名稱套用國際化網域名稱 \(Internationalized Domain Name，IDN\) 剖析。|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|指定是否要將國際資源識別項 \(International Resource Identifier，IRI\) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|指定如何針對特定配置剖析 <xref:System.Uri>。|  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[組態](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|包含所有命名空間的設定。|  
  
## 備註  
 `uri` 項目包含 <xref:System.Net> 命名空間中類別所使用 <xref:System.Uri> 類別成員的設定。  這些設定會設定 IRI 和 IDN 的支援。  
  
## 範例  
  
### 描述  
 在下列程式碼範例中，會說明 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的組態。  範例也會清楚所有配置設定，然後加入 HTTP 配置非逸出百分比編碼路徑分隔符號的支援。  
  
### 程式碼  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## 請參閱  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)