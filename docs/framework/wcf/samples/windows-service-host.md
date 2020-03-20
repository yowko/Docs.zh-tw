---
title: Windows 服務主機
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143521"
---
# <a name="windows-service-host"></a>Windows 服務主機
此示例演示託管 Windows 服務中託管的 Windows 通信基礎 （WCF） 服務。 Windows 服務使用 **"控制台**"中的服務小程式進行控制，並可配置為在系統重新開機後自動啟動。 範例是由用戶端程式與 Windows 服務程式所組成。 服務會實作為 .exe 程式並包含專屬的裝載程式碼。 在其他裝載環境中，例如 Windows 處理序啟用服務 (WAS) 或 Internet Information Services (IIS)，就不需要撰寫裝載程式碼。

> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。

> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 在這個服務完成建置後，它必須像任何其他 Windows 服務一樣使用 Installutil.exe 公用程式安裝。 如果要變更服務，就必須先以 `installutil /u` 將它解除安裝。 這個範例中包含的 Setup.bat 和 Cleanup.bat 檔是用來安裝和啟動 Windows 服務，以及關閉和解除安裝 Windows 服務的命令。 僅當 Windows 服務正在運行時，WCF 服務才能回應用戶端。 如果使用 **"控制台**"中的服務小程式停止 Windows 服務並運行用戶端，則用戶端嘗試<xref:System.ServiceModel.EndpointNotFoundException>訪問該服務時將發生異常。 如果重新啟動 Windows 服務然後重新執行用戶端，就可成功進行通訊。  
  
 服務代碼包括安裝程式類、實現 I計算機協定的 WCF 服務實現類以及充當執行階段主機的 Windows 服務類。 繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別，會允許 Installutil.exe 工具將程式當做 NT 服務進行安裝。 服務實現類`WcfCalculatorService`是實現基本服務協定的 WCF 服務。 此 WCF 服務託管在稱為`WindowsCalculatorService`的 Windows 服務類中。 為了限定為 Windows 服務，此類別會繼承自 <xref:System.ServiceProcess.ServiceBase>，並且實作 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 和 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法。 使用 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 時，會建立並開啟型別為 <xref:System.ServiceModel.ServiceHost> 的 `WcfCalculatorService` 物件。 使用 <xref:System.ServiceProcess.ServiceBase.OnStop> 時，會呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 物件的 <xref:System.ServiceModel.ServiceHost> 方法來關閉 ServiceHost。 主機的基本位址使用[\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)元素進行配置，該元素是[\<基底位址>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)的子項目，它是[\<主機>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)元素的子項，該元素是[\<服務>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)元素的子項目。  
  
 定義的終結點使用基本位址和[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。 下列範例會示範設定基底位址，以及會公開 (Expose) CalculatorService 的端點。  
  
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
  
1. 確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 構建解決方案後，從提升的 Visual Studio 2012 命令提示符運行安裝程式.bat，使用 Installutil.exe 工具安裝 Windows 服務。 此時該服務就會出現在 [服務] 中。  
  
4. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 主控與持續性範例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
