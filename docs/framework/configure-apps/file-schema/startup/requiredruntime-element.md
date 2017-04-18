---
title: "&lt;requiredRuntime&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requiredRuntime> 項目"
  - "容器標記, <requiredRuntime> 項目"
  - "requiredRuntime 項目"
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;requiredRuntime&gt; 項目
指定應用程式只支援 Common Language Runtime 1.0 版。  
  
## 語法  
  
```  
  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`version`|選擇性屬性。<br /><br /> 字串值，指定這個應用程式所支援的 .NET Framework 版本。  字串值必須符合 .NET Framework 安裝根目錄下存在的目錄名稱。  不會剖析字串值的內容。|  
|`safemode`|選擇性屬性。<br /><br /> 指定 Runtime 啟始程式碼 \(Startup Code\) 是否搜尋登錄以決定 Runtime 版本。|  
  
## Safemode 屬性  
  
|值|描述|  
|-------|--------|  
|`false`|執行階段啟始程式碼會在登錄中查詢。  此為預設值。|  
|`true`|執行階段啟始程式碼不會在登錄中查詢。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`startup`|包含 `<requiredRuntime>` 項目。|  
  
## 備註  
 建置為只支援 Runtime 1.0 版的應用程式時，必須使用 `<requiredRuntime>` 項目。  使用 Runtime 1.1 \(含\) 以後版本建置的應用程式必須使用 `<supportedRuntime>` 項目。  
  
> [!NOTE]
>  如果您使用 [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 函式指定組態檔，則必須為該執行階段的所有版本使用 `<requiredRuntime>` 項目。  當您使用 [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 時，會忽略 `<supportedRuntime>` 項目。  
  
 `version` 屬性字串必須符合指定的 .NET Framework 版本的安裝資料夾名稱。  這個字串並不會被解譯。  如果 Runtime 啟始程式碼沒有找到相符的資料夾，則不會載入 Runtime；啟始程式碼會顯示錯誤訊息，並且結束。  
  
> [!NOTE]
>  裝載在 Microsoft Internet Explorer 中的應用程式啟始程式碼會忽略 `<requiredRuntime>` 項目。  
  
## 範例  
 下列範例顯示如何在組態檔中指定 Runtime 版本。  
  
```  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## 請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/zh-tw/c376208d-980d-42b4-865b-fbe0d9cc97c2)