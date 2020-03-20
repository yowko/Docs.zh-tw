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
# <a name="wmi-provider"></a><span data-ttu-id="7cd68-102">WMI 提供者</span><span class="sxs-lookup"><span data-stu-id="7cd68-102">WMI Provider</span></span>
<span data-ttu-id="7cd68-103">此示例演示如何使用 WCF 中內置的 Windows 管理檢測 （WMI） 提供程式在運行時從 Windows 通信基礎 （WCF） 服務收集資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="7cd68-104">此外，這個範例還會示範如何將使用者定義的 WMI 物件新增至服務。</span><span class="sxs-lookup"><span data-stu-id="7cd68-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="7cd68-105">該示例啟動入門的 WMI 提供程式[，並](../../../../docs/framework/wcf/samples/getting-started-sample.md)演示如何在運行時從`ICalculator`服務收集資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="7cd68-106">WMI 是 Microsoft 對「Web 架構企業管理」(Web-Based Enterprise Management，WBEM) 標準的實作。</span><span class="sxs-lookup"><span data-stu-id="7cd68-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="7cd68-107">有關 WMI SDK 的詳細資訊，請參閱[Windows 管理檢測](/windows/desktop/WmiSdk/wmi-start-page)。</span><span class="sxs-lookup"><span data-stu-id="7cd68-107">For more information about the WMI SDK, see [Windows Management Instrumentation](/windows/desktop/WmiSdk/wmi-start-page).</span></span> <span data-ttu-id="7cd68-108">WBEM 是一套業界標準，說明應用程式如何將管理測試設備公開至外部管理工具。</span><span class="sxs-lookup"><span data-stu-id="7cd68-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="7cd68-109">WCF 實現 WMI 提供程式，該元件通過 WBEM 相容的介面在運行時公開檢測。</span><span class="sxs-lookup"><span data-stu-id="7cd68-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="7cd68-110">管理工具可以在執行階段，透過介面連接到服務。</span><span class="sxs-lookup"><span data-stu-id="7cd68-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="7cd68-111">WCF 公開服務的屬性，如位址、綁定、行為和攔截器。</span><span class="sxs-lookup"><span data-stu-id="7cd68-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="7cd68-112">內建 WMI 提供者可以在應用程式的組態檔中啟動。</span><span class="sxs-lookup"><span data-stu-id="7cd68-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="7cd68-113">這是通過[\<系統中的診斷>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)`wmiProviderEnabled`的屬性完成的>。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7cd68-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="7cd68-114">這個組態項目會公開 WMI 介面。</span><span class="sxs-lookup"><span data-stu-id="7cd68-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="7cd68-115">現在，管理應用程式可以透過這個介面進行連線，並存取應用程式的管理測試設備。</span><span class="sxs-lookup"><span data-stu-id="7cd68-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="7cd68-116">自訂 WMI 物件</span><span class="sxs-lookup"><span data-stu-id="7cd68-116">Custom WMI Object</span></span>  
 <span data-ttu-id="7cd68-117">新增 WMI 物件至服務，可以將使用者定義的資訊連同內建 WMI 提供者的資訊一併公開。</span><span class="sxs-lookup"><span data-stu-id="7cd68-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="7cd68-118">只要使用 Installutil.exe 應用程式將服務的結構描述發行至 WMI，就能達成這個目的。</span><span class="sxs-lookup"><span data-stu-id="7cd68-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="7cd68-119">有關完成這項作業的指示以及詳細資料，可在本主題結尾的安裝指示中找到。</span><span class="sxs-lookup"><span data-stu-id="7cd68-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="7cd68-120">存取 WMI 資訊</span><span class="sxs-lookup"><span data-stu-id="7cd68-120">Accessing WMI Information</span></span>  

<span data-ttu-id="7cd68-121">您可以使用各種不同的方式來存取 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-121">WMI data can be accessed in many different ways.</span></span> <span data-ttu-id="7cd68-122">Microsoft 為腳本、視覺化基本應用程式、C++應用程式和 .NET 框架提供 WMI API。</span><span class="sxs-lookup"><span data-stu-id="7cd68-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the .NET Framework.</span></span> <span data-ttu-id="7cd68-123">有關詳細資訊，請參閱使用[WMI](/windows/desktop/wmisdk/using-wmi)。</span><span class="sxs-lookup"><span data-stu-id="7cd68-123">For more information, see [Using WMI](/windows/desktop/wmisdk/using-wmi).</span></span>
  
 <span data-ttu-id="7cd68-124">這個範例會使用兩個 Java 指令碼：一個是用來列舉電腦上執行的服務及其部分屬性，而第二個則是用來檢視使用者定義的 WMI 資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-124">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="7cd68-125">指令碼會開啟 WMI 提供者的連線、剖析資料，以及顯示收集到的資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-125">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="7cd68-126">啟動示例以創建 WCF 服務的正在運行的實例。</span><span class="sxs-lookup"><span data-stu-id="7cd68-126">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="7cd68-127">在服務執行的同時，請於命令提示字元中使用下列命令來執行各個 Java 指令碼：</span><span class="sxs-lookup"><span data-stu-id="7cd68-127">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```console  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="7cd68-128">指令碼會存取服務中包含的測試設備，然後產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7cd68-128">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
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
  
 <span data-ttu-id="7cd68-129">接下來，請執行第二個 Java 指令碼以顯示使用者定義的 WMI 資料：</span><span class="sxs-lookup"><span data-stu-id="7cd68-129">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```console  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="7cd68-130">指令碼會存取服務中包含的使用者定義測試設備，然後產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="7cd68-130">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```console
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="7cd68-131">這項輸出顯示電腦上有一個服務在執行。</span><span class="sxs-lookup"><span data-stu-id="7cd68-131">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="7cd68-132">服務會公開一個實作 `ICalculator` 合約的端點。</span><span class="sxs-lookup"><span data-stu-id="7cd68-132">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="7cd68-133">端點所實作之行為和繫結的設定會以訊息堆疊個別項目的總和列出。</span><span class="sxs-lookup"><span data-stu-id="7cd68-133">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="7cd68-134">WMI 並不限於公開 WCF 基礎結構的管理檢測。</span><span class="sxs-lookup"><span data-stu-id="7cd68-134">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="7cd68-135">應用程式也可以透過同樣的機制公開自己網域的特定資料項目。</span><span class="sxs-lookup"><span data-stu-id="7cd68-135">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="7cd68-136">WMI 是適用於檢查並控制 Web 服務的統一機制。</span><span class="sxs-lookup"><span data-stu-id="7cd68-136">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7cd68-137">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="7cd68-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7cd68-138">確保已[為 Windows 通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="7cd68-138">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7cd68-139">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="7cd68-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7cd68-140">您可以對裝載目錄中的 service.dll 檔案執行 InstallUtil.exe (InstallUtil.exe 的預設位置在 "%WINDIR%\Microsoft.NET\Framework\v4.0.30319")，將服務結構描述發行至 WMI。</span><span class="sxs-lookup"><span data-stu-id="7cd68-140">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="7cd68-141">只有在已對 service.dll 檔案進行變更時，才需要執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="7cd68-141">This step only needs to be executed when changes have been made to the service.dll file.</span></span>
  
4. <span data-ttu-id="7cd68-142">要在單電腦或跨電腦配置中運行示例，請按照[運行 Windows 通信基礎示例中的](../../../../docs/framework/wcf/samples/running-the-samples.md)說明操作。</span><span class="sxs-lookup"><span data-stu-id="7cd68-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7cd68-143">如果在安裝ASP.NET後安裝了 WCF，則可能需要運行"%WINDIR%\*Microsoft.Net_Framework_v3.0_Windows 通信基礎_服務模型reg.exe"-r -x 授予 ASPNET 帳戶發佈 WMI 物件的許可權。</span><span class="sxs-lookup"><span data-stu-id="7cd68-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5. <span data-ttu-id="7cd68-144">請使用命令 `cscript EnumerateServices.js` 或 `cscript EnumerateCustomObjects.js`，檢視由範例透過 WMI 呈現的資料。</span><span class="sxs-lookup"><span data-stu-id="7cd68-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7cd68-145">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="7cd68-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7cd68-146">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="7cd68-146">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="7cd68-147">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="7cd68-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7cd68-148">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="7cd68-148">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="7cd68-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cd68-149">See also</span></span>

- <span data-ttu-id="7cd68-150">[AppFabric 監控範例](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7cd68-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
