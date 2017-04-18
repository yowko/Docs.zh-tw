---
title: "Windows 服務主機 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "NT 服務"
  - "NT 服務主機範例 [Windows Communication Foundation]"
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# Windows 服務主機
這個範例會示範裝載於受管理 Windows 服務中的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。Windows 服務是使用 \[**控制台**\] 中的 \[服務\] 小程式控制，並且可以設定為在系統重新開機後自動啟動。範例是由用戶端程式與 Windows 服務程式所組成。服務會實作為 .exe 程式並包含專屬的裝載程式碼。在其他裝載環境中，例如 Windows 處理序啟用服務 \(WAS\) 或 Internet Information Services \(IIS\)，就不需要撰寫裝載程式碼。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 在這個服務完成建置後，它必須像任何其他 Windows 服務一樣使用 Installutil.exe 公用程式安裝。如果要變更服務，就必須先以 `installutil /u` 將它解除安裝。這個範例中包含的 Setup.bat 和 Cleanup.bat 檔是用來安裝和啟動 Windows 服務，以及關閉和解除安裝 Windows 服務的命令。只有在執行 Windows 服務的情況下，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務才會回應用戶端。如果您從 \[**控制台**\] 中使用 \[服務\] 小程式停止 Windows 服務，並接著執行用戶端，則當用戶端嘗試存取此服務時將會發生 <xref:System.ServiceModel.EndpointNotFoundException> 例外狀況。如果重新啟動 Windows 服務然後重新執行用戶端，就可成功進行通訊。  
  
 這段服務程式碼包含安裝程式類別、會實作 ICalculator 合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務實作類別，以及做為執行階段主機的 Windows 服務類別。繼承自 <xref:System.Configuration.Install.Installer> 的安裝程式類別，會允許 Installutil.exe 工具將程式當做 NT 服務進行安裝。服務實作類別 `WcfCalculatorService` 是實作基本服務合約的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。這個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務是裝載於稱為 `WindowsCalculatorService` 的 Windows 服務類別中。為了限定為 Windows 服務，此類別會繼承自 <xref:System.ServiceProcess.ServiceBase>，並且實作 [OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 和 <xref:System.ServiceProcess.ServiceBase.OnStop> 方法。使用 [OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> 時，會建立並開啟型別為 `WcfCalculatorService` 的 <xref:System.ServiceModel.ServiceHost> 物件。使用 <xref:System.ServiceProcess.ServiceBase.OnStop> 時，會呼叫 <xref:System.ServiceModel.ServiceHost> 物件的 <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> 方法來關閉 ServiceHost。設定主機基底位址的方式是使用 [\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) 項目，這個項目是 [\<baseAddresses\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md) 的子系，而 [\<Host \- 主應用程式\>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) 項目、[\<服務\>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) 項目依此類推，前一項目相繼為其後項目的子系。  
  
 所定義的端點會使用基底位址以及 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。下列範例會示範設定基底位址，以及會公開 \(Expose\) CalculatorService 的端點。  
  
```  
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
  
 當您執行範例時，作業要求和回應會顯示在服務與用戶端主控台視窗中。在每個主控台視窗中按下 ENTER 鍵，即可關閉服務與用戶端。  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C\# 或 Visual Basic .NET 版本，請遵循[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  在建置方案後，從提高權限的 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 命令提示字元執行 Setup.bat，以便使用 Installutil.exe 工具來安裝 Windows 服務。此時該服務就會出現在 \[服務\] 中。  
  
4.  若要在單一或跨電腦的組態中執行本範例，請遵循[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。  
  
## 請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)