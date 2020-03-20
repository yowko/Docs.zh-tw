---
title: WMI 提供者
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: 04fdbb7efcae6fdbb78f467352e6106ac5218799
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183194"
---
# <a name="wmi-provider"></a>WMI 提供者
此示例演示如何使用 WCF 中內置的 Windows 管理檢測 （WMI） 提供程式在運行時從 Windows 通信基礎 （WCF） 服務收集資料。 此外，這個範例還會示範如何將使用者定義的 WMI 物件新增至服務。 該示例啟動入門的 WMI 提供程式[，並](../../../../docs/framework/wcf/samples/getting-started-sample.md)演示如何在運行時從`ICalculator`服務收集資料。  
  
 WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。 有關 WMI SDK 的詳細資訊，請參閱[Windows 管理檢測](/windows/desktop/WmiSdk/wmi-start-page)。 WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。  
  
 WCF 實現 WMI 提供程式，該元件通過 WBEM 相容的介面在運行時公開檢測。 管理工具可以在執行階段，透過介面連接到服務。 WCF 公開服務的屬性，如位址、綁定、行為和攔截器。  
  
 內建 WMI 提供者可以在應用程式的組態檔中啟動。 這是通過[\<系統中的診斷>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)`wmiProviderEnabled`的屬性完成的>。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
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

您可以使用各種不同的方式來存取 WMI 資料。 Microsoft 為腳本、視覺化基本應用程式、C++應用程式和 .NET 框架提供 WMI API。 有關詳細資訊，請參閱使用[WMI](/windows/desktop/wmisdk/using-wmi)。
  
 這個範例會使用兩個 Java 指令碼：一個是用來列舉電腦上執行的服務及其部分屬性，而第二個則是用來檢視使用者定義的 WMI 資料。 指令碼會開啟 WMI 提供者的連線、剖析資料，以及顯示收集到的資料。  
  
 啟動示例以創建 WCF 服務的正在運行的實例。 在服務執行的同時，請於命令提示字元中使用下列命令來執行各個 Java 指令碼：  
  
```console  
cscript EnumerateServices.js  
```  
  
 指令碼會存取服務中包含的測試設備，然後產生下列輸出：  
  
```console  
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
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 指令碼會存取服務中包含的使用者定義測試設備，然後產生下列輸出：  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 這項輸出顯示電腦上有一個服務在執行。 服務會公開一個實作 `ICalculator` 合約的端點。 端點所實作之行為和繫結的設定會以訊息堆疊個別項目的總和列出。  
  
 WMI 並不限於公開 WCF 基礎結構的管理檢測。 應用程式也可以透過同樣的機制公開自己網域的特定資料項目。 WMI 是適用於檢查並控制 Web 服務的統一機制。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 確保已[為 Windows 通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3. 您可以對裝載目錄中的 service.dll 檔案執行 InstallUtil.exe (InstallUtil.exe 的預設位置在 "%WINDIR%\Microsoft.NET\Framework\v4.0.30319")，將服務結構描述發行至 WMI。 只有在已對 service.dll 檔案進行變更時，才需要執行這個步驟。
  
4. 要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。  
  
    > [!NOTE]
    > 如果在安裝ASP.NET後安裝了 WCF，則可能需要運行"%WINDIR%*Microsoft.Net_Framework_v3.0_Windows 通信基礎_服務模型reg.exe"-r -x 授予 ASPNET 帳戶發佈 WMI 物件的許可權。  
  
5. 請使用命令 `cscript EnumerateServices.js` 或 `cscript EnumerateCustomObjects.js`，檢視由範例透過 WMI 呈現的資料。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a>另請參閱

- [AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
