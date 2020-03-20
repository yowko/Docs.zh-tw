---
title: WCF 服務的簡化組態
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183346"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="132b7-102">WCF 服務的簡化組態</span><span class="sxs-lookup"><span data-stu-id="132b7-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="132b7-103">此示例演示如何使用 Windows 通信基礎 （WCF） 實現和配置典型服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="132b7-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="132b7-104">這個範例是所有其他基本技術範例的基礎。</span><span class="sxs-lookup"><span data-stu-id="132b7-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="132b7-105">此服務公開用於與服務通信的終結點，使用 .NET 框架 4 中的簡化配置。</span><span class="sxs-lookup"><span data-stu-id="132b7-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="132b7-106">在 .NET 框架 4 之前，終結點通常在設定檔 （Web.config） 中定義，如以下示例配置代碼所示。</span><span class="sxs-lookup"><span data-stu-id="132b7-106">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="132b7-107">在 .NET 框架`<service>`4 中，該元素是可選的。</span><span class="sxs-lookup"><span data-stu-id="132b7-107">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="132b7-108">當服務沒有定義任何端點時，每個基底位址的端點和實作的合約都會加入到服務中。</span><span class="sxs-lookup"><span data-stu-id="132b7-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="132b7-109">基底位址會附加到合約名稱以判斷端點，而繫結則取決於位址配置。</span><span class="sxs-lookup"><span data-stu-id="132b7-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="132b7-110">下列程式碼範例示範簡化的組態檔。</span><span class="sxs-lookup"><span data-stu-id="132b7-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="132b7-111">配置後，同一台電腦上的用戶端可以訪問`http://localhost/servicemodelsamples/service.svc`該服務。</span><span class="sxs-lookup"><span data-stu-id="132b7-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="132b7-112">為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="132b7-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="132b7-113">根據預設，此服務不會公開任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="132b7-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="132b7-114">因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。</span><span class="sxs-lookup"><span data-stu-id="132b7-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="132b7-115">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="132b7-115">To use this sample</span></span>  
  
1. <span data-ttu-id="132b7-116">確保已為 Windows[通信基礎示例執行一次性設置過程](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="132b7-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="132b7-117">要生成解決方案，請按照生成 Windows[通信基礎示例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的說明進行操作。</span><span class="sxs-lookup"><span data-stu-id="132b7-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="132b7-118">遵循下列步驟執行範例：</span><span class="sxs-lookup"><span data-stu-id="132b7-118">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="132b7-119">按右鍵**服務**專案並選擇 **"設置為啟動"專案**，然後按**Ctrl_F5**。</span><span class="sxs-lookup"><span data-stu-id="132b7-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="132b7-120">等待主控台輸出確認服務已啟動且在執行中。</span><span class="sxs-lookup"><span data-stu-id="132b7-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="132b7-121">按右鍵 **"用戶端**專案"並選擇 **"設置為啟動專案**"，然後按**Ctrl_F5**。</span><span class="sxs-lookup"><span data-stu-id="132b7-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="132b7-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="132b7-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="132b7-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="132b7-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="132b7-124">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="132b7-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="132b7-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="132b7-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="132b7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="132b7-126">See also</span></span>

- <span data-ttu-id="132b7-127">[AppFabric 管理範例](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="132b7-127">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="132b7-128">簡化設定</span><span class="sxs-lookup"><span data-stu-id="132b7-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
