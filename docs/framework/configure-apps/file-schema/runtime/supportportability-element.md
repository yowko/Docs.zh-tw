---
title: "&lt;supportPortability&gt; 項目 | Microsoft Docs"
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
helpviewer_keywords: 
  - "<supportPortability> 項目"
  - "supportPortability 項目"
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# &lt;supportPortability&gt; 項目
指定應用程式可以停用為了達到應用程式可攜性而將組件視為相等的預設行為，以參考兩個不同 .NET Framework 實作中的同一個組件。  
  
## 語法  
  
```  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|PKT|必要屬性。<br /><br /> 以字串形式指定受影響組件的公開金鑰語彙基元。|  
|enabled|選擇性屬性。<br /><br /> 指定是否應該啟用指定的 .NET Framework 組件實作之間的可攜性支援。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|true|啟用指定 .NET Framework 組件實作之間的可攜性支援。  這是預設值。|  
|false|停用指定 .NET Framework 組件實作之間的可攜性支援。  這可讓應用程式參考指定組件的多個實作。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
  
## 備註  
 自 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，會自動提供支援給可使用兩個 .NET Framework 中任何一個的應用程式，例如可使用 .NET Framework 實作或 .NET Framework for Silverlight 實作。  組件繫結器會將特定 .NET Framework 組件的兩個實作視為相等。  在某些情況下，此應用程式的可攜性功能會發生問題。  在這些案例中，`<supportPortability>` 項目可用來停用此功能。  
  
 其中一個此類案例是組件，該組件同時參考特定參考組件的 .NET Framework 實作和 .NET Framework for Silverlight 實作。  例如，以 Windows Presentation Foundation \(WPF\) 撰寫的 XAML 設計工具需參考 WPF 桌面實作 \(適合設計人員的使用者介面\) 與 Silverlight 實作隨附的 WPF 的子集。  預設情況下，不同的參考會造成編譯器錯誤，因為組件繫結會將兩個組件視為相等。  這個項目會停用預設行為，並允許編譯成功。  
  
> [!IMPORTANT]
>  您必須使用 `/appconfig` 編譯器選項指定包含這個項目的 app.config 檔案的位置，編譯器才能將資訊傳遞至 Common Language Runtime 的組件繫結邏輯。  
  
## 範例  
 下列範例讓應用程式能夠參考 .NET Framework 實作，和存在於兩個實作中任何 .NET Framework 組件其 Silverlight 實作的 .NET Framework。  `/appconfig` 編譯器選項必須用來指定此 app.config 檔案的位置。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [\/appconfig \(C\# 編譯器選項\)](http://msdn.microsoft.com/library/ee523958.aspx)   
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/zh-tw/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)