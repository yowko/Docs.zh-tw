---
title: WCF 服務的簡化組態
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 47af8dcba35ba31f25597c946596b0cbcac93b4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304255"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="e5032-102">WCF 服務的簡化組態</span><span class="sxs-lookup"><span data-stu-id="e5032-102">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="e5032-103">此範例示範如何實作與設定一般服務和用戶端使用 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="e5032-103">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e5032-104">這個範例是所有其他基本技術範例的基礎。</span><span class="sxs-lookup"><span data-stu-id="e5032-104">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="e5032-105">公開端點以便與服務進行通訊的這個服務會在 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 中使用簡化的組態。</span><span class="sxs-lookup"><span data-stu-id="e5032-105">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].</span></span> <span data-ttu-id="e5032-106">在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 之前，端點通常是在組態檔 (Web.config) 中定義的，如下列範例組態程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="e5032-106">Prior to [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
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
  
 <span data-ttu-id="e5032-107">在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 中，`<service>` 項目是選用的。</span><span class="sxs-lookup"><span data-stu-id="e5032-107">In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], the `<service>` element is optional.</span></span> <span data-ttu-id="e5032-108">當服務沒有定義任何端點時，每個基底位址的端點和實作的合約都會加入到服務中。</span><span class="sxs-lookup"><span data-stu-id="e5032-108">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="e5032-109">基底位址會附加到合約名稱以判斷端點，而繫結則取決於位址配置。</span><span class="sxs-lookup"><span data-stu-id="e5032-109">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="e5032-110">下列程式碼範例示範簡化的組態檔。</span><span class="sxs-lookup"><span data-stu-id="e5032-110">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="e5032-111">在設定，可以存取的服務在 `http://localhost/servicemodelsamples/service.svc` 在同一部電腦上的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e5032-111">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="e5032-112">為了讓遠端電腦上的用戶端存取服務，這時必須指定完整網域名稱，而不要指定 localhost。</span><span class="sxs-lookup"><span data-stu-id="e5032-112">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="e5032-113">根據預設，此服務不會公開任何中繼資料。</span><span class="sxs-lookup"><span data-stu-id="e5032-113">The service does not expose metadata by default.</span></span> <span data-ttu-id="e5032-114">因此，服務會開啟 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。</span><span class="sxs-lookup"><span data-stu-id="e5032-114">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
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
  
### <a name="to-use-this-sample"></a><span data-ttu-id="e5032-115">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="e5032-115">To use this sample</span></span>  
  
1. <span data-ttu-id="e5032-116">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e5032-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e5032-117">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e5032-117">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e5032-118">遵循下列步驟執行範例：</span><span class="sxs-lookup"><span data-stu-id="e5032-118">Run the sample by following these steps:</span></span>  
  
    1.  <span data-ttu-id="e5032-119">以滑鼠右鍵按一下**服務**專案，然後選取**設定為啟始專案**，然後按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e5032-119">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2.  <span data-ttu-id="e5032-120">等待主控台輸出確認服務已啟動且在執行中。</span><span class="sxs-lookup"><span data-stu-id="e5032-120">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3.  <span data-ttu-id="e5032-121">以滑鼠右鍵按一下**用戶端**專案，然後選取**設定為啟始專案**，然後按**Ctrl + F5**。</span><span class="sxs-lookup"><span data-stu-id="e5032-121">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5032-122">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e5032-122">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e5032-123">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e5032-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e5032-124">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="e5032-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e5032-125">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e5032-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="e5032-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5032-126">See also</span></span>

- [<span data-ttu-id="e5032-127">AppFabric 管理範例</span><span class="sxs-lookup"><span data-stu-id="e5032-127">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
- [<span data-ttu-id="e5032-128">簡化設定</span><span class="sxs-lookup"><span data-stu-id="e5032-128">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
