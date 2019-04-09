---
title: 追蹤和訊息記錄
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: ba4428bad6662928ddc1830c8998dd5f5b6b9bbe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186572"
---
# <a name="tracing-and-message-logging"></a>追蹤和訊息記錄
這個範例示範如何啟用追蹤和訊息記錄。 產生的追蹤和訊息記錄則會使用檢視[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="tracing"></a>追蹤  
 Windows Communication Foundation (WCF) 會使用在定義的追蹤機制<xref:System.Diagnostics>命名空間。 在這個追蹤模型中，應用程式實作的追蹤來源會產生追蹤資料。 每個來源都是以名稱來識別。 追蹤消費者會為他們要擷取資訊的追蹤來源建立追蹤接聽項。 若要接收追蹤資料，就必須建立追蹤來源的接聽項。 在 WCF 中，做法是藉由將下列程式碼新增至服務或用戶端的組態檔中，藉由設定服務模型追蹤來源`switchValue`:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 如需詳細的追蹤來源的詳細資訊，請參閱中的追蹤來源 > 一節[設定追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)主題。  
  
## <a name="activity-tracing-and-propagation"></a>活動追蹤和傳播  
 擁有`ActivityTracing`啟用並`propagateActivity`設為`true`在`system.ServiceModel`用戶端和服務的追蹤來源會提供追蹤的處理 （活動），邏輯單位內的相互關聯跨端點 （內的活動透過活動傳輸），以及跨多個端點 （透過活動識別碼傳播） 活動。  
  
 這三種機制 (活動、傳輸和傳播) 可以協助您使用 [服務追蹤檢閱器] 工具，迅速找到錯誤的根本原因。 如需詳細資訊，請參閱 <<c0> [ 使用服務追蹤檢視器檢視相互關聯的追蹤和疑難排解](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。  
  
 您可以建立使用者定義的活動追蹤，來延伸 ServiceModel 所提供的追蹤。 使用者定義的活動追蹤允許使用者建立追蹤活動，以進行下列工作：  
  
-   將追蹤集合成工作邏輯單位的群組。  
  
-   透過傳輸和傳播將活動相互關聯。  
  
-   降低 （例如，記錄檔的磁碟空間成本） 的 WCF 追蹤的效能成本。  
  
 如需有關使用者定義的活動追蹤的詳細資訊，請參閱[擴充追蹤](../../../../docs/framework/wcf/samples/extending-tracing.md)範例。  
  
## <a name="message-logging"></a>訊息記錄  
 用戶端和服務的任何 WCF 應用程式，可以啟用訊息記錄。 若要啟用訊息記錄，您必須將下列程式碼新增至用戶端或服務：  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 記錄訊息時，追蹤類型將依據是在用戶端或在伺服器上追蹤而定。 例如，在用戶端，傳送給用戶端的「新增」訊息會受到 "TransportWrite" 類型的追蹤，然而在服務上，相同的訊息則會受到 "TransportRead" 類型的追蹤。  
  
 設定追蹤接聽項，方式是將下列程式碼新增至用戶端的 App.config 檔案或服務的 Web.config 檔案的 <xref:System.Diagnostics> 區段：  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 在組態檔內指定的目標目錄中，會使用 XML 格式來記錄訊息。  
  
> [!NOTE]
>  如果一開始並未建立記錄目錄，就不會建立追蹤檔。 請確定目錄 C:\logs\ 存在，不然就在接聽項組態中指定其他記錄目錄。 如需詳細資訊，請參閱本文件結尾的初始安裝指示。  
  
 如需訊息記錄的詳細資訊，請參閱[設定訊息記錄](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)主題。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  在執行追蹤和訊息記錄範例前，請先建立可供服務將 .svclog 檔寫入的 C:\logs\ 目錄。 這個目錄名稱會在組態檔中定義為所要記錄之追蹤和訊息的路徑，而您可以變更此名稱。 請提供使用者對記錄目錄的網路服務寫入權限。  
  
3.  若要建置方案的 C#、 c + + 或 Visual Basic.NET 版本，請依照下列中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>另請參閱

- [追蹤](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [AppFabric 監控範例](https://go.microsoft.com/fwlink/?LinkId=193959)
