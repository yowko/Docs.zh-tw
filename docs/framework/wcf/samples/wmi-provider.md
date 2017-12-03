---
title: "WMI 提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d5537c636edfa557c75298c5cf63127f10f4827
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="wmi-provider"></a>WMI 提供者
這個範例示範如何在執行階段使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 內建的 Windows Management Instrumentation (WMI) 提供者從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務收集資料。 此外，這個範例還會示範如何將使用者定義的 WMI 物件新增至服務。 此範例會啟動的 WMI 提供者[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)並示範如何收集資料，從`ICalculator`服務在執行階段。  
  
 WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。 如需有關 WMI SDK 的詳細資訊，請參閱[Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx)。 WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會實作 WMI 提供者，這是可透過 WBEM 相容介面，在執行階段公開測試設備的元件。 管理工具可以在執行階段，透過介面連接到服務。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會公開服務的屬性，例如位址、繫結、行為和接聽項。  
  
 內建 WMI 提供者可以在應用程式的組態檔中啟動。 這透過完成`wmiProviderEnabled`屬性[\<診斷 >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)中[ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)區段，如下列範例所示組態：  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 這個組態項目會公開 WMI 介面。 現在，管理應用程式可以透過這個介面進行連線，並存取應用程式的管理測試設備。  
  
## <a name="custom-wmi-object"></a>自訂 WMI 物件  
 新增 WMI 物件至服務，可以將使用者定義的資訊連同內建 WMI 提供者的資訊一併公開。 只要使用 Installutil.exe 應用程式將服務的結構描述發行至 WMI，就能達成這個目的。 有關完成這項作業的指示以及詳細資料，可在本主題結尾的安裝指示中找到。  
  
## <a name="accessing-wmi-information"></a>存取 WMI 資訊  
 您可以使用各種不同方式來存取 WMI 資料。 Microsoft 為指令碼、[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 應用程式、C++ 應用程式和 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供 WMI API (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp)。  
  
 這個範例會使用兩個 Java 指令碼：一個是用來列舉電腦上執行的服務及其部分屬性，而第二個則是用來檢視使用者定義的 WMI 資料。 指令碼會開啟 WMI 提供者的連線、剖析資料，以及顯示收集到的資料。  
  
 請啟動範例以建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的執行中執行個體。 在服務執行的同時，請於命令提示字元中使用下列命令來執行各個 Java 指令碼：  
  
```  
cscript EnumerateServices.js  
```  
  
 指令碼會存取服務中包含的測試設備，然後產生下列輸出：  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 接下來，請執行第二個 Java 指令碼以顯示使用者定義的 WMI 資料：  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 指令碼會存取服務中包含的使用者定義測試設備，然後產生下列輸出：  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 這項輸出顯示電腦上有一個服務在執行。 服務會公開一個實作 `ICalculator` 合約的端點。 端點所實作之行為和繫結的設定會以訊息堆疊個別項目的總和列出。  
  
 WMI 不限於只是公開 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構的管理測試設備。 應用程式也可以透過同樣的機制公開自己網域的特定資料項目。 WMI 是適用於檢查並控制 Web 服務的統一機制。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  確認您已經執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  您可以對裝載目錄中的 service.dll 檔案執行 InstallUtil.exe (InstallUtil.exe 的預設位置在 "%WINDIR%\Microsoft.NET\Framework\v4.0.30319")，將服務結構描述發行至 WMI。 只有在已對 service.dll 檔案進行變更時，才需要執行這個步驟。 如需詳細資訊，請參閱＜如何：為檢測的應用程式發行結構描述至 WMI＞一節中的＜透過檢測應用程式提供管理資訊＞，網址為http://msdn2.microsoft.com/library/ms186147.aspx。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
    > [!NOTE]
    >  如果是在安裝 ASP.NET 之後安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，您可能需要執行 "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x，以授與 ASPNET 帳戶發行 WMI 物件的權限。  
  
5.  請使用命令 `cscript EnumerateServices.js` 或 `cscript EnumerateCustomObjects.js`，檢視由範例透過 WMI 呈現的資料。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](http://go.microsoft.com/fwlink/?LinkId=193959)
