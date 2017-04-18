---
title: "&lt;switches&gt; 的 &lt;add&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<switches> 的 <add> 項目"
  - "<switches> 的 add 項目"
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;switches&gt; 的 &lt;add&gt; 項目
指定設定追蹤參數的層級。  
  
## 語法  
  
```  
<add name="switch name"  
     value="value"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|**name**|必要屬性。<br /><br /> 指定參數的名稱。  這個屬性的值會對應至傳遞至參數 \(Switch\) 建構函式的 *displayName* 參數 \(Parameter\)。|  
|**值**|必要屬性。<br /><br /> 指定參數的層級。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`switches`|包含追蹤參數和設定追蹤參數的層級。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
  
## 備註  
 您可以將追蹤參數放在組態檔中，以變更參數的層級。  如果參數是 <xref:System.Diagnostics.BooleanSwitch>，您可以開啟或關閉這個參數。  如果參數是 <xref:System.Diagnostics.TraceSwitch>，您可以為其指派不同的層級，以指定應用程式輸出的追蹤或偵錯訊息類型。  
  
## 範例  
 以下範例顯示如何使用 **\<add\>** 項目，將 `General` 追蹤參數設為 [TraceLevel.Error](frlrfSystemDiagnosticsTraceLevelClassTopic) 層級，並且啟用 `Data` 布林追蹤參數。  
  
```  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.Switch>   
 <xref:System.Diagnostics.TraceSwitch>   
 <xref:System.Diagnostics.BooleanSwitch>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)