---
title: "追蹤與訊息記錄的建議設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 追蹤與訊息記錄的建議設定
本主題將說明不同作業環境中，建議的追蹤和訊息記錄設定。  
  
## 實際執行環境的建議設定  
 如果您使用 WCF 追蹤來源，請將實際執行環境的 `switchValue` 設為 Warning。  如果您使用 WCF `System.ServiceModel` 追蹤來源，請將 `switchValue` 屬性設為 `Warning` 以及將 `propagateActivity` 屬性設為 `true`。  如果您使用的是使用者定義的追蹤來源，請將 `switchValue` 屬性設為 `Warning, ActivityTracing`。  這項操作可使用[組態編輯器工具 \(SvcConfigEditor.exe\)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)，以手動的方式完成。  如果您無法預測對效能的衝擊，則可在之前提到的所有案例中，將 `switchValue` 屬性設為 `Information`，如此就會產生相當大量的追蹤資料。  以下範例將示範這些建議的設定。  
  
```  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## 部署或偵錯的建議設定  
 針對部署或偵錯環境，請選擇用於使用者定義或 `System.ServiceModel` 追蹤來源的 `Information` 或 `Verbose`，以及 `ActivityTracing`。  若要增強偵錯功能，則應同時將額外的追蹤來源 \(`System.ServiceModel.MessageLogging`\) 加入組態中，以啟用訊息記錄。  請注意，`switchValue` 屬性不會影響此追蹤來源。  
  
 以下範例將示範建議的設定，其中會使用利用了 `XmlWriterTraceListener` 的共用接聽項。  
  
```  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## 使用 WMI 修改設定  
 您可以使用 WMI 在執行階段變更組態設定 \(藉由啟用組態中的 `wmiProviderEnabled` 屬性，如之前的組態範例中所示範\)。  例如，您可以在 CIM Studio 中使用 WMI，將執行階段的追蹤來源層級從 Warning 變更為 Information。  您應注意的是，以此方式執行即時偵錯的效能成本可能會相當高。  如需有關使用 WMI 的詳細資訊，請參閱[使用 Windows Management Instrumentation 進行診斷](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)主題。  
  
## 啟用 ASP.NET 追蹤中的相互關聯事件  
 ASP.NET 事件不會設定相互關聯 ID \(ActivityID\)，除非 ASP.NET 事件追蹤開啟。  若要正確看到相互關聯事件，您必須移至 \[**開始**\]，然後 \[**執行**\]，再輸入 **cmd** 來叫用命令主控台，然後在命令主控台中使用下列命令來開啟 ASP.NET 事件追蹤，  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 若要關閉 ASP.NET 事件追蹤，請使用下列命令，  
  
```  
logman stop mytrace -ets  
```  
  
## 請參閱  
 [使用 Windows Management Instrumentation 進行診斷](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)