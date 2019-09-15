---
title: ETW 追蹤
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: fb1a1dc77ee6a7be25aade18f76f89464bef0387
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989952"
---
# <a name="etw-tracing"></a>ETW 追蹤
這個範例示範如何使用 Event Tracing for Windows (ETW) 和範例隨附的 `ETWTraceListener`，以實作端對端 (E2E) 追蹤。 此範例是以[消費者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)為基礎，並包含 ETW 追蹤。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 這個範例假設您已熟悉[追蹤和訊息記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)。  
  
 <xref:System.Diagnostics> 追蹤模型中的每個追蹤來源都可以有多個追蹤接聽項，這些接聽項將決定追蹤資料的位置和方式。 接聽項的類型會定義記錄追蹤資料的格式。 下列程式碼範例示範如何將接聽項新增至組態。  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 使用這個接聽項之前，必須先啟動 ETW 追蹤工作階段。 您可以使用 Logman.exe 或 Tracelog.exe 啟動這個工作階段。 此範例隨附可供您設定 ETW 追蹤工作階段的 SetupETW.bat 檔案，以及可用來關閉工作階段與完成記錄檔的 CleanupETW.bat 檔案。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。 如需這些工具的詳細資訊，請參閱<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 使用 ETWTraceListener 時，追蹤會記錄在二進位的 .etl 檔案中。 開啟 ServiceModel 追蹤之後，所有產生的追蹤都會出現在同一個檔案中。 使用[服務追蹤檢視器工具（svctraceviewer.exe .exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)來查看 .etl 和 .svclog 記錄檔。 此檢視器會建立系統的端對端檢視，讓您能夠從訊息的來源至其目的端及消費點追蹤該訊息。  
  
 ETW 追蹤接聽項支援循環記錄。 若要啟用這項功能，請移至 [開始`cmd` ]、[**執行**]，然後輸入以啟動命令主控台。 以記錄檔名稱取代下列命令中的 `<logfilename>` 參數。  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` 和 `-max` 參數是選擇項， 可以分別指定二進位循環格式以及最多 1000MB 的記錄檔大小上限。 `-p` 參數會用來指定追蹤提供者。 在範例中，`"{411a0819-c24b-428c-83e2-26b41091702e}"` 即是「XML ETW 範例提供者」的 GUID。  
  
 若要啟動工作階段，請輸入下列命令。  
  
```console  
logman start Wcf  
```  
  
 完成記錄之後，您可以使用下列命令停止工作階段。  
  
```console  
logman stop Wcf  
```  
  
 這個程式會產生二進位迴圈記錄檔，您可以使用您選擇的工具來處理，包括[服務追蹤檢視器工具（svctraceviewer.exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)或 Tracerpt。  
  
 您也可以參閱[迴圈追蹤](../../../../docs/framework/wcf/samples/circular-tracing.md)範例，以取得替代接聽程式執行迴圈記錄的詳細資訊。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建立方案，請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。  
  
    > [!NOTE]
    > 若要使用 RegisterProvider.bat、SetupETW.bat 與 CleanupETW.bat 命令，您必須使用本機系統管理員帳戶執行。 如果您使用的是 [!INCLUDE[wv](../../../../includes/wv-md.md)] 或更新版本，也必須使用更高的權限來執行命令提示字元。 若要這樣做，請以滑鼠右鍵按一下命令提示字元圖示，然後按一下 [以**系統管理員身分執行**]。  
  
3. 執行範例前，請先在用戶端和伺服器上執行 RegisterProvider.bat。 這會設定產生的 ETWTracingSampleLog.etl 檔案，以產生可由服務追蹤檢視器讀取的追蹤。 您可以在 C:\logs 資料夾中找到這個檔案。 如果此資料夾不存在，必須先建立一個才能產生追蹤。 然後，在用戶端和伺服器電腦上執行 SetupETW.bat，以便開始 ETW 追蹤工作階段。 SetupETW.bat 檔案可以在 CS\Client 資料夾中找到。  
  
4. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
5. 當您完成範例時，請執行 CleanupETW.bat 以完成建立 ETWTracingSampleLog.etl 檔案的工作。  
  
6. 在 [服務追蹤檢視器] 中開啟 ETWTracingSampleLog.etl 檔案。 系統會提示您將二進位格式的檔案儲存為 .svclog 檔。  
  
7. 在 [服務追蹤檢視器] 中開啟新建立的 .svclog 檔，以檢視 ETW 和 ServiceModel 追蹤。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> 如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監視範例](https://go.microsoft.com/fwlink/?LinkId=193959)
