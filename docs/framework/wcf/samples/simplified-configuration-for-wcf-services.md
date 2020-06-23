---
title: WCF 服務的簡化組態
description: 瞭解如何使用 WCF 來執行和設定一般服務和用戶端。 服務會使用設定檔中指定的端點進行通訊。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246214"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="fffe1-104">WCF 服務的簡化組態</span><span class="sxs-lookup"><span data-stu-id="fffe1-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="fffe1-105">這個範例會示範如何使用 Windows Communication Foundation （WCF）來執行和設定一般服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="fffe1-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="fffe1-106">這個範例是所有其他基本技術範例的基礎。</span><span class="sxs-lookup"><span data-stu-id="fffe1-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="fffe1-107">此服務會公開用來與服務通訊的端點，並使用 .NET Framework 4 中的簡化設定。</span><span class="sxs-lookup"><span data-stu-id="fffe1-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="fffe1-108">在 .NET Framework 4 之前，端點通常是在設定檔（Web.config）中定義，如下列範例設定程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fffe1-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="fffe1-109">在 .NET Framework 4 中， `<service>` 元素是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="fffe1-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="fffe1-110">當服務沒有定義任何端點時，每個基底位址的端點和實作的合約都會加入到服務中。</span><span class="sxs-lookup"><span data-stu-id="fffe1-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="fffe1-111">基底位址會附加到合約名稱以判斷端點，而繫結則取決於位址配置。</span><span class="sxs-lookup"><span data-stu-id="fffe1-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="fffe1-112">下列程式碼範例示範簡化的組態檔。</span><span class="sxs-lookup"><span data-stu-id="fffe1-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="fffe1-113">如已設定，服務可 `http://localhost/servicemodelsamples/service.svc` 由同一部電腦上的用戶端存取。</span><span class="sxs-lookup"><span data-stu-id="fffe1-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="fffe1-114">為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="fffe1-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="fffe1-115">根據預設，此服務不會公開任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="fffe1-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="fffe1-116">因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。</span><span class="sxs-lookup"><span data-stu-id="fffe1-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="fffe1-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="fffe1-117">To use this sample</span></span>  
  
1. <span data-ttu-id="fffe1-118">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="fffe1-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fffe1-119">若要建立方案，請依照[建立 Windows Communication Foundation 範例](building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="fffe1-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="fffe1-120">遵循下列步驟執行範例：</span><span class="sxs-lookup"><span data-stu-id="fffe1-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="fffe1-121">以滑鼠右鍵按一下**服務**專案，並選取 [**設定為啟始專案**]，然後按下**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="fffe1-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="fffe1-122">等待主控台輸出確認服務已啟動且在執行中。</span><span class="sxs-lookup"><span data-stu-id="fffe1-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="fffe1-123">以滑鼠右鍵按一下**用戶端**專案，並選取 [**設定為啟始專案**]，然後按下**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="fffe1-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fffe1-124">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fffe1-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="fffe1-125">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fffe1-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fffe1-126">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="fffe1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fffe1-127">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fffe1-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="fffe1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fffe1-128">See also</span></span>

- <span data-ttu-id="fffe1-129">[AppFabric 管理範例](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="fffe1-129">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="fffe1-130">簡化設定</span><span class="sxs-lookup"><span data-stu-id="fffe1-130">Simplified Configuration</span></span>](../simplified-configuration.md)
