---
title: "&lt;source&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#source"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<source> 項目"
  - "source 項目"
ms.assetid: ecf86505-735d-4844-aaba-266fdd134218
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;source&gt; 項目
指定會啟始追蹤訊息的追蹤來源。  
  
## 語法  
  
```  
<source>   
  <listeners>...</listeners>  
</source>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`name`|選擇性屬性。<br /><br /> 指定追蹤來源的名稱。|  
|`switchName`|選擇性屬性。<br /><br /> 指定應用程式中追蹤參數執行個體的名稱。  如果此參數未在 `<switches>` 項目中識別，則此值會指定該參數的層級。|  
|`switchType`|選擇性屬性。<br /><br /> 指定追蹤參數的型別。  如果有的話，則此型別必須是有效的類別名稱，且不能是空字串。|  
|`extraAttribute`|選擇性屬性。<br /><br /> 指定由追蹤來源的特定屬性的值<xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A>為追蹤來源的方法。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<listeners\>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|包含收集、儲存和傳送訊息的接聽程式。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定收集、存放和傳送訊息的追蹤接聽程式，以及設定追蹤參數的層級。|  
|`sources`|包含會啟始追蹤訊息的追蹤來源。|  
  
## 備註  
 這個項目可以用於電腦組態檔 \(Machine.config\) 和應用程式組態檔。  
  
## 範例  
 下列範例將示範如何使用 `<source>`  項目加入追蹤來源 `mySource`，以及針對名為 `sourceSwitch` 的來源參數設定層級。  可寫入追蹤資訊的主控台追蹤接聽項會加入到主控台中。  
  
```  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>    
  </system.diagnostics>   
</configuration>  
```  
  
## 請參閱  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)   
 [Trace Switches](../../../../../docs/framework/debug-trace-profile/trace-switches.md)