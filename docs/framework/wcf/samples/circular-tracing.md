---
title: "循環追蹤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 循環追蹤
這個範例會示範循環緩衝區追蹤接聽項的實作。實際執行服務的常見案例是產生可長時間使用的服務以及可在低階進行的追蹤記錄。這些服務會耗用大量的磁碟空間。在進行服務疑難排解時，追蹤記錄中最近的資料往往最切合問題的解決。這個範例將示範實作循環緩衝區追蹤接聽項，其中會將最近的追蹤保存在磁碟上，最多到某個可設定的資料數量。這個範例是以[使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎，並附有自訂追蹤接聽項。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例假設您熟悉[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例，而且已閱讀[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例提供的相關文件。  
  
## 循環緩衝區追蹤接聽項  
 實作「循環緩衝區追蹤接聽項」的基本概念是產生兩個檔案，而這兩個檔案可以各自儲存多達追蹤記錄資料總共所需數量的一半。接聽項會先建立一個檔案，再寫入該檔案直到資料大小上限的一半為止，然後於此時切換到第二個檔案。當接聽項寫入到達第二個檔案的限制時，便會將新的追蹤覆寫到第一個檔案。  
  
 這個接聽項是衍生自 `XmlWriteTraceListener`，而且可讓您使用[服務追蹤檢視器工具 \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) 來檢視記錄。當您嘗試檢視記錄時，只要在 \[服務追蹤檢視器\] 工具中同時開啟這兩個記錄檔，就可以輕易地將兩個記錄檔重新合併。\[服務追蹤檢視器\] 工具會自動排序追蹤，讓它們依照正確的順序出現。  
  
## 組態  
 您可以為接聽項與來源項目新增下列程式碼，以便將服務設定為使用循環緩衝區追蹤接聽項。在循環追蹤接聽項的組態中設定 `maxFileSizeKB` 屬性，可以指定檔案大小的上限。這點會在下列程式碼中示範。  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
  
```  
  
#### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## 請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)