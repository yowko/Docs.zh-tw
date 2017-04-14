---
title: "&lt;httpWebRequest&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<httpWebRequest> 項目"
  - "httpWebRequest 項目"
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: 18
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 18
---
# &lt;httpWebRequest&gt; 項目 (網路設定)
自訂 Web 要求參數。  
  
## 語法  
  
```  
  
      <httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|**屬性**|**描述**|  
|------------|------------|  
|`maximumResponseHeadersLength`|指定回應標頭的最大長度，以 KB 為單位。  預設值為 64。  \-1 表示不會在回應標頭上附加大小限制。|  
|`maximumErrorResponseLength`|指定錯誤回應的最大長度，以 KB 為單位。  預設值為 64。  \-1 表示不會在錯誤回應上附加大小限制。|  
|`maximumUnauthorizedUploadLength`|指定上載的最大長度，回應未經授權的錯誤碼，以位元組為單位。  預設值為 \-1。  \-1 的值表示不會對上載加諸任何大小限制。|  
|`useUnsafeHeaderParsing`|指定是否啟用不安全的標頭解析。  預設值是 `false`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|**項目**|**描述**|  
|------------|------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
 根據預設，.NET Framework 會對 URI 剖析嚴格地強制執行 RFC 2616。  某些伺服器回應可能在禁止欄位中包含控制字元，這將會使 <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> 方法擲回 <xref:System.Net.WebException>。  如果 **useUnsafeHeaderParsing** 設定為 **true**，則在這種情況下，<xref:System.Net.HttpWebRequest.GetResponse?displayProperty=fullName> 不會擲回，但是應用程式會很容易遭受數種 URI 剖析的攻擊。  最好的解決方式就是變更伺服器，讓回應不會包含控制字元。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例顯示如何指定大於一般值的最大標頭長度。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)