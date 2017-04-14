---
title: "&lt;idn&gt; 項目 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;idn&gt; 項目 (Uri 設定)
指定是否要對網域名稱套用國際化網域名稱 \(Internationalized Domain Name，IDN\) 剖析。  
  
## 結構描述階層架構  
 [\<configuration\> 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri\> 項目 \(Uri 設定\)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn\>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## 語法  
  
```  
<idn  
  enabled="All|AllExceptIntranet|None"  
/idn>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|**元素**|**說明**|  
|------------|------------|  
|`enabled`|指定是否要對網域名稱套用國際化網域名稱 \(IDN\) 剖析，預設值為 \[無\]。|  
  
### 子項目  
 無  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|內含設定，指定 .NET Framework 如何處理使用統一資源識別元 \(URI\) 表示的網址。|  
  
## 備註  
 現有的 <xref:System.Uri> 類別已在 .NET Framework 3.5、3.0 SP1 和 2.0 SP1 中擴充，以提供國際資源識別項 \(International Resource Identifiers，IRI\) 和國際化網域名稱 \(Internationalized Domain Names，IDN\) 的支援。  目前的使用者不會看到 .NET Framework 2.0 的行為變化，除非使用者指定啟用對 IRI 和 IDN 的支援。  這可確保應用程式與舊版 .NET Framework 的相容性。  
  
 若要啟用 IRI 的支援，則需要進行下列兩項變更：  
  
1.  將下行加入 .NET Framework 2.0 目錄的 machine.config 檔案中  
  
    ```  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  指定是否要對網域名稱套用國際化網域名稱 \(IDN\) 剖析，以及是否應該套用 IRI 剖析規則。  這項變更可以在 machine.config 或 app.config 檔案中進行。  
  
 根據使用的 DNS 伺服器，IDN 有三種可能值：  
  
-   idn enabled \= All  
  
     這個值會將任何 Unicode 網域名稱轉換成 Punycode 的對等名稱 \(IDN 名稱\)。  
  
-   idn enabled \= AllExceptIntranet  
  
     這個值會將所有不位於近端內部網路的 Unicode 網域名稱轉換為使用 Punycode 的對等名稱 \(IDN 名稱\)。  此例中，若要在近端內部網路上處理國際性名稱，則用於內部網路的 DNS 伺服器應該支援 Unicode 名稱解析。  
  
-   idn enabled \= None  
  
     這個值不會轉換任何 Unicode 網域名稱即可使用 Punycode。  這是預設值，與 .NET Framework 2.0 的行為一致。  
  
 啟用 IDN 會將網域名稱內的所有 Unicode 標籤 \(Label\) 轉換成 Punycode 的對等名稱。  Punycode 名稱只包含 ASCII 字元，且開頭一律為 xn\-\- 前置字元。  這麼做的原因是要支援網際網路上現有的 DNS 伺服器，因為大多數的 DNS 伺服器僅支援 ASCII 字元 \(請參閱 RFC 3940\)。  
  
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
 <xref:System.Configuration.IdnElement?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)