---
title: "&lt;trace&gt; 適用之 &lt;listeners&gt; 的 &lt;remove&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<remove> 項目"
  - "remove 項目"
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;trace&gt; 適用之 &lt;listeners&gt; 的 &lt;remove&gt; 項目
從 **Listeners** 集合移除接聽程式。  
  
## 語法  
  
```  
  
<remove name="listener name" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|**name**|必要屬性。<br /><br /> 要從 **Listeners** 集合移除的接聽程式名稱。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定收集、存放及傳送訊息的接聽程式。  接聽程式將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`trace`|設定 ASP.NET 追蹤服務。|  
  
## 備註  
  
> [!NOTE]
>  從 `Listeners` 集合移除 <xref:System.Diagnostics.DefaultTraceListener> 會改變 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>、<xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> 和 <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> 方法的行為。  手動呼叫 `Assert` 或 `Fail` 方法通常會導致訊息方塊出現；不過，如果 <xref:System.Diagnostics.DefaultTraceListener> 不在 `Listeners` 集合中，則不會顯示此訊息方塊。  
  
## 範例  
 以下範例顯示的是如何從追蹤 **Listeners** 集合移除預設追蹤接聽程式。  
  
```  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Diagnostics.TraceListener>   
 <xref:System.Diagnostics.DefaultTraceListener>   
 <xref:System.Diagnostics.TextWriterTraceListener>   
 <xref:System.Diagnostics.EventLogTraceListener>   
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)