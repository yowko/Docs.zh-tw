---
title: 循環追蹤
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: ce39a5d1b65bad78ff67154a7d8b62c2f19b1fa9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="circular-tracing"></a>循環追蹤
這個範例會示範循環緩衝區追蹤接聽項的實作。 實際執行服務的常見案例是產生可長時間使用的服務以及可在低階進行的追蹤記錄。 這些服務會耗用大量的磁碟空間。 在進行服務疑難排解時，追蹤記錄中最近的資料往往最切合問題的解決。 這個範例將示範實作循環緩衝區追蹤接聽項，其中會將最近的追蹤保存在磁碟上，最多到某個可設定的資料數量。 這個範例根據[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)和包含自訂追蹤接聽程式。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此範例假設您已熟悉[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例並已閱讀所提供的文件[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)範例。  
  
## <a name="circular-buffer-trace-listener"></a>循環緩衝區追蹤接聽項  
 實作「循環緩衝區追蹤接聽項」的基本概念是產生兩個檔案，而這兩個檔案可以各自儲存多達追蹤記錄資料總共所需數量的一半。 接聽項會先建立一個檔案，再寫入該檔案直到資料大小上限的一半為止，然後於此時切換到第二個檔案。 當接聽項寫入到達第二個檔案的限制時，便會將新的追蹤覆寫到第一個檔案。  
  
 此接聽程式是衍生自`XmlWriteTraceListener`並允許記錄檔，以檢視與[服務追蹤檢視器工具 (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。 當您嘗試檢視記錄時，只要在 [服務追蹤檢視器] 工具中同時開啟這兩個記錄檔，就可以輕易地將兩個記錄檔重新合併。 [服務追蹤檢視器] 工具會自動排序追蹤，讓它們依照正確的順序出現。  
  
## <a name="configuration"></a>組態  
 您可以為接聽項與來源項目新增下列程式碼，以便將服務設定為使用循環緩衝區追蹤接聽項。 在循環追蹤接聽項的組態中設定 `maxFileSizeKB` 屬性，可以指定檔案大小的上限。 這點會在下列程式碼中示範。  
  
```xml  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
