---
title: "擴充追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# 擴充追蹤
這個範例示範如何在用戶端與服務程式碼中撰寫使用者定義的活動追蹤，以擴充 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 追蹤功能。這樣可以讓使用者建立追蹤活動，並將追蹤分組成工作的邏輯單位 \(Logical Unit\)。也可以透過傳輸 \(在相同的端點內\) 以及傳播 \(跨端點\) 方式來關聯活動。在此範例中，用戶端與服務都會啟用追蹤。如需如何透過用戶端與服務組態檔啟用追蹤的詳細資訊，請參閱[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)。  
  
 此範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## 追蹤與活動傳播  
 使用者定義的活動追蹤可以讓使用者建立自己的追蹤活動，並將追蹤分組成工作邏輯單位、透過傳輸與傳播來關聯活動，以及降低 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 追蹤的效能成本 \(例如，記錄檔的磁碟空間成本\)。  
  
### 新增自訂來源  
 使用者定義的追蹤可以同時新增至用戶端與服務程式碼。將追蹤來源新增至用戶端或服務組態檔，便可使這些自訂追蹤記錄並顯示在[服務追蹤檢視器工具 \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)中。下列程式碼示範如何將名為 `ServerCalculatorTraceSource` 之使用者定義的追蹤來源新增至組態檔。  
  
```  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### 關聯活動  
 若要直接關聯跨端點的活動，在 `System.ServiceModel` 追蹤來源中的 `propagateActivity` 屬性必須設定為 `true`。此外，若要不經過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 活動來傳播追蹤，這時必須關閉 ServiceModel 活動追蹤。這項設定將如下列程式碼範例所示。  
  
> [!NOTE]
>  關閉 ServiceModel 活動追蹤的方式不同於指定追蹤層級 \(以設定為 Off 的 `switchValue` 屬性表示\)。  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### 降低效能成本  
 將 `System.ServiceModel` 追蹤來源中的 `ActivityTracing` 設定為 Off 時會產生追蹤檔，其中只包含使用者定義的活動追蹤，而不包含任何 ServiceModel 活動追蹤。這樣會使記錄檔的大小變小許多。但是，這樣就沒辦法關聯 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 處理追蹤。  
  
##### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
## 請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)