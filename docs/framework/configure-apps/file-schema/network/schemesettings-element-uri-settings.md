---
title: "&lt;schemeSettings&gt; 項目 (Uri 設定) | Microsoft Docs"
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
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# &lt;schemeSettings&gt; 項目 (Uri 設定)
指定如何針對特定配置剖析 <xref:System.Uri>。  
  
## 語法  
  
```  
  
      <schemeSettings>   
</schemeSettings>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無  
  
### 子項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[加入](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|加入結構描述名稱的結構描述設定。|  
|[clear](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|清除所有現有的結構描述設定。|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|移除結構描述名稱的結構描述設定。|  
  
### 父項目  
  
|**元素**|**說明**|  
|------------|------------|  
|[URI](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|內含設定，指定 .NET Framework 如何處理使用統一資源識別元 \(URI\) 表示的網址。|  
  
## 備註  
 根據預設，<xref:System.Uri?displayProperty=fullName> 類別會在執行路徑壓縮前，取消逸出百分比編碼路徑分隔符號。  這會實作為安全機制，以防禦下列攻擊：  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 如果此 URI 傳遞到未正確處理百分比編碼字元的模組，可能會導致伺服器執行下列命令：  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 因此，<xref:System.Uri?displayProperty=fullName> 類別會先取消逸出路徑分隔符號，然後再套用路徑壓縮。  將惡意 URL 傳遞至 <xref:System.Uri?displayProperty=fullName> 類別建構函式的結果，會產生下列 URI：  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 可以使用特定結構描述的 schemeSettings 組態選項，將這個預設行為修改為不取消逸出百分比編碼路徑分隔符號。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例示範 <xref:System.Uri> 類別所使用的組態，該組態支援不逸出的 HTTP 結構描述的百分比編碼路徑分隔符號。  
  
```  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間|System|  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## 請參閱  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=fullName>   
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection?displayProperty=fullName>   
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=fullName>   
 <xref:System.GenericUriParserOptions?displayProperty=fullName>   
 <xref:System.Uri?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)