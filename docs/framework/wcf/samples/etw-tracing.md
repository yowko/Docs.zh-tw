---
title: ETW 追蹤
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183708"
---
# <a name="etw-tracing"></a>ETW 追蹤
這個範例示範如何使用 Event Tracing for Windows (ETW) 和範例隨附的 `ETWTraceListener`，以實作端對端 (E2E) 追蹤。 該示例基於["入門"，](../../../../docs/framework/wcf/samples/getting-started-sample.md)包括 ETW 跟蹤。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 此示例假定您熟悉[跟蹤和消息日誌記錄](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md)。  
  
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
> 此範例的安裝程序與建置指示位於本主題的結尾。 有關這些工具的詳細資訊，請參閱<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 使用 ETWTraceListener 時，追蹤會記錄在二進位的 .etl 檔案中。 開啟 ServiceModel 追蹤之後，所有產生的追蹤都會出現在同一個檔案中。 使用[服務跟蹤檢視器工具 （SvcTraceViewer.exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)查看 .etl 和 .svclog 日誌檔。 此檢視器會建立系統的端對端檢視，讓您能夠從訊息的來源至其目的端及消費點追蹤該訊息。  
  
 ETW 追蹤接聽項支援循環記錄。 要啟用此功能，請轉到 **"開始****"，運行**並`cmd`鍵入以啟動命令主控台。 以記錄檔名稱取代下列命令中的 `<logfilename>` 參數。  
  
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
  
 此過程生成二進位迴圈日誌，您可以使用您選擇的工具進行處理，包括[服務跟蹤檢視器工具 （SvcTraceViewer.exe）](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)或 Tracerpt。  
  
 您還可以查看[迴圈跟蹤](../../../../docs/framework/wcf/samples/circular-tracing.md)示例，瞭解有關執行迴圈日誌記錄的替代攔截器的詳細資訊。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確保您已為 Windows[通信基礎示例執行了一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 要生成解決方案，請按照生成 Windows[通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的說明進行操作。  
  
    > [!NOTE]
    > 若要使用 RegisterProvider.bat、SetupETW.bat 與 CleanupETW.bat 命令，您必須使用本機系統管理員帳戶執行。 如果您使用的是 Windows Vista 或更高版本，則還必須使用較高的權限運行命令提示符。 為此，請按右鍵命令提示圖示，然後按一下"**以管理員身份運行**"。  
  
3. 執行範例前，請先在用戶端和伺服器上執行 RegisterProvider.bat。 這會設定產生的 ETWTracingSampleLog.etl 檔案，以產生可由服務追蹤檢視器讀取的追蹤。 您可以在 C:\logs 資料夾中找到這個檔案。 如果此資料夾不存在，必須先建立一個才能產生追蹤。 然後，在用戶端和伺服器電腦上執行 SetupETW.bat，以便開始 ETW 追蹤工作階段。 SetupETW.bat 檔案可以在 CS\Client 資料夾中找到。  
  
4. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
5. 當您完成範例時，請執行 CleanupETW.bat 以完成建立 ETWTracingSampleLog.etl 檔案的工作。  
  
6. 在 [服務追蹤檢視器] 中開啟 ETWTracingSampleLog.etl 檔案。 系統會提示您將二進位格式的檔案儲存為 .svclog 檔。  
  
7. 在 [服務追蹤檢視器] 中開啟新建立的 .svclog 檔，以檢視 ETW 和 ServiceModel 追蹤。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
