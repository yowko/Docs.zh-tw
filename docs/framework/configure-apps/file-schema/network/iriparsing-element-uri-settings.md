---
title: "&lt;iriParsing&gt; 項目 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;iriParsing&gt; 項目 (Uri 設定)
指定是否要將國際資源識別項 \(International Resource Identifier，IRI\) 剖析套用至 <xref:System.Uri>，以及是否應該套用 IRI 剖析規則。  
  
## 結構描述階層架構  
 [\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing\>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## 語法  
  
```  
<idn  
  enabled="true|false"  
/idn>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**元素**|**說明**|  
|------------|------------|  
|`enabled`|指定是否啟用 IRI 剖析。  預設值是 `false`。|  
  
### 子項目  
 無  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|內含設定，指定 .NET Framework 如何處理使用統一資源識別元 \(URI\) 表示的網址。|  
  
## 備註  
 現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5、3.0 SP1 和 2.0 SP1 中擴充，以提供國際資源識別項 \(International Resource Identifier，IRI\) 和國際化網域名稱 \(Internationalized Domain Names，IDN\) 的支援。  目前的使用者不會看到 .NET Framework 2.0 的行為變化，除非使用者指定啟用對 IRI 和 IDN 的支援。  這可確保應用程式與舊版 .NET Framework 的相容性。  
  
 若要啟用 IRI 的支援，則需要進行下列兩項變更：  
  
1.  將下行加入 .NET Framework 2.0 目錄的 machine.config 檔案中  
  
    ```  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否要套用 IRI 剖析規則。  這項變更可以在 machine.config 或 app.config 檔案中進行。  
  
 啟用 IRI 剖析 \(iriParsing enabled \= `true`\) 會根據 RFC 3987 中最新的 IRI 規則執行正規化和字元檢查。  預設值為 `false`，並且會根據 RFC 2396 和 RFC 3986 \(適用於 IPv6 常值\) 執行正規化和字元檢查。  
  
### 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
  
### 說明  
 在下列程式碼範例中，會說明 <xref:System.Uri> 類別用來支援 IRI 剖析和 IDN 名稱的組態。  
  
### 程式碼  
  
```  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Configuration.IriParsingElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)