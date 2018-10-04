---
title: Windows 服務主機
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 65797863fc8187ffebbcb660e9fb285bfa1aabd0
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583850"
---
# <a name="windows-service-host"></a>Windows 服務主機
這個範例會示範裝載在 managed Windows 服務的 Windows Communication Foundation (WCF) 服務。 Windows 服務使用中的 [服務] 小程式來控制**控制台中**和可以設定為在系統重新開機後自動啟動。 範例是由用戶端程式與 Windows 服務程式所組成。 服務會實作為 .exe 程式並包含專屬的裝載程式碼。 在其他裝載環境中，例如 Windows 處理序啟用服務 (WAS) 或 Internet Information Services (IIS)，就不需要撰寫裝載程式碼。

> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。

> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 在這個服務完成建置後，它必須像任何其他 Windows 服務一樣使用 Installutil.exe 公用程式安裝。 如果要變更服務，就必須先以 `installutil /u` 將它解除安裝。 這個範例中包含的 Setup.bat 和 Cleanup.bat 檔是用來安裝和啟動 Windows 服務，以及關閉和解除安裝 Windows 服務的命令。 如果 Windows 服務執行用戶端只可以回應的 WCF 服務。 如果您使用從 [服務] 小程式停止 Windows 服務**控制台中**並執行用戶端，<xref:System.ServiceModel.EndpointNotFoundException>用戶端嘗試存取服務時，就會發生例外狀況。 如果重新啟動 Windows 服務然後重新執行用戶端，就可成功進行通訊。  
  
 服務程式碼包含安裝程式類別，它會實作 ICalculator 合約的 WCF 服務實作類別和做為執行階段主應用程式的 Windows 服務類別。 繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別，會允許 Installutil.exe 工具將程式當做 NT 服務進行安裝。 服務實作類別`WcfCalculatorService`，是實作基本的服務合約的 WCF 服務。 此裝載 WCF 服務的 Windows 服務類別，稱為內`WindowsCalculatorService`。 為了限定為 Windows 服務，此類別會繼承自 <xref:System.ServiceProcess.ServiceBase>，並且實作 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 和 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法。 使用 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 時，會建立並開啟型別為 <xref:System.ServiceModel.ServiceHost> 的 `WcfCalculatorService` 物件。 使用 <xref:System.ServiceProcess.ServiceBase.OnStop> 時，會呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 物件的 <xref:System.ServiceModel.ServiceHost> 方法來關閉 ServiceHost。 使用設定主機的基底位址[\<新增 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)項目，這是子系的[ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)，這是子系[ \<主機 >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)項目，這是子系的[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)項目。  
  
 定義的端點會使用基底位址以及[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。 下列範例會示範設定基底位址，以及會公開 (Expose) CalculatorService 的端點。  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。 在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  解決方案之後已經建立的從提升權限來安裝 Windows 服務使用 Installutil.exe 工具 Visual Studio 2012 命令提示字元執行 Setup.bat。 此時該服務就會出現在 [服務] 中。  
  
4.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](https://go.microsoft.com/fwlink/?LinkId=193961)
