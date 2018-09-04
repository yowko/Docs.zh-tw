---
title: 階層式組態模型
ms.date: 03/30/2017
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
ms.openlocfilehash: 8ca9b01eb022e2e2ab940866a6230e8227ceb2dc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499337"
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="9ec11-102">階層式組態模型</span><span class="sxs-lookup"><span data-stu-id="9ec11-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="9ec11-103">此範例示範如何針對服務實作組態檔的階層。</span><span class="sxs-lookup"><span data-stu-id="9ec11-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="9ec11-104">它也會示範如何從階層中較高的層級繼承繫結、服務行為與端點行為。</span><span class="sxs-lookup"><span data-stu-id="9ec11-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="9ec11-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="9ec11-105">Sample details</span></span>  
 <span data-ttu-id="9ec11-106">其中一個功能開發中的 WCF[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]是階層式組態模型中的改進。</span><span class="sxs-lookup"><span data-stu-id="9ec11-106">One of the features developed for WCF in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="9ec11-107">階層組態模型的範例是由 Machine.config -> Rootweb.config -> Web.config 所定義的範例。在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 中，於組態階層之較上層中定義的那些繫結與行為都會在沒有明確組態的情況下，加入至您的服務。</span><span class="sxs-lookup"><span data-stu-id="9ec11-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="9ec11-108">此範例示範如何能夠透過依賴在電腦或應用程式層級定義的組態項目，簡化您的服務組態。</span><span class="sxs-lookup"><span data-stu-id="9ec11-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="9ec11-109">這個範例由三個階層層級中定義的九個服務所組成。</span><span class="sxs-lookup"><span data-stu-id="9ec11-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="9ec11-110">`Service1` 位於根目錄。</span><span class="sxs-lookup"><span data-stu-id="9ec11-110">`Service1` is at the root.</span></span> <span data-ttu-id="9ec11-111">`Service2` 和 `Service3` 從 `Service1` 繼承預設元素。</span><span class="sxs-lookup"><span data-stu-id="9ec11-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="9ec11-112">`Service4`、`Service5`、`Service6` 和 `Service7` 是在階層的第三個層級定義的，且從 `Service3` 繼承預設項目。</span><span class="sxs-lookup"><span data-stu-id="9ec11-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="9ec11-113">最後，`Service10` 和 `Service11` 則位於階層的第四個層級。</span><span class="sxs-lookup"><span data-stu-id="9ec11-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="9ec11-114">所有服務都會實作 `IDesc` 合約。</span><span class="sxs-lookup"><span data-stu-id="9ec11-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="9ec11-115">以下是 `IDesc` 介面的定義，這個定義會顯示在此介面中公開的方法。</span><span class="sxs-lookup"><span data-stu-id="9ec11-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="9ec11-116">`IDesc` 介面是在 Service1.cs 中定義的。</span><span class="sxs-lookup"><span data-stu-id="9ec11-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```csharp  
// Define a service contract  
[ServiceContract(Namespace="http://Microsoft.Samples.ConfigHierarchicalModel")]  
public interface IDesc  
{  
    [OperationContract]  
    List<string> ListEndpoints();  
    [OperationContract]  
    List<string> ListServiceBehaviors();  
    [OperationContract]  
    List<string> ListEndpointBehaviors();  
}  
```  
  
 <span data-ttu-id="9ec11-117">由服務針對這些方法進行的實作相當直接。</span><span class="sxs-lookup"><span data-stu-id="9ec11-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="9ec11-118">`ListEndpoints` 會逐一查看所有服務端點，並傳回服務所擁有之所有端點的清單。</span><span class="sxs-lookup"><span data-stu-id="9ec11-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="9ec11-119">`ListServiceBehaviors` 會逐一查看加入至服務的所有行為，並傳回與服務相關聯之所有服務行為的清單。</span><span class="sxs-lookup"><span data-stu-id="9ec11-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="9ec11-120">`ListEndpointBehaviors` 以類似於 `ListServiceBehaviors` 的方式運作，但它會傳回端點行為的清單。</span><span class="sxs-lookup"><span data-stu-id="9ec11-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="9ec11-121">這個實作可讓用戶端了解服務公開多少端點，以及哪些服務行為和端點行為已加入至服務。</span><span class="sxs-lookup"><span data-stu-id="9ec11-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="9ec11-122">已經當做範例一部分實作的用戶端會將服務參考加入至方案中的所有服務，並針對每個服務顯示這些項目。</span><span class="sxs-lookup"><span data-stu-id="9ec11-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="9ec11-123">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="9ec11-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="9ec11-124">若要執行用戶端</span><span class="sxs-lookup"><span data-stu-id="9ec11-124">To run the client</span></span>  
  
1.  <span data-ttu-id="9ec11-125">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 ConfigHierarchicalModel.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="9ec11-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="9ec11-126">如果用戶端專案還未設定為啟始專案，請遵循下列步驟進行。</span><span class="sxs-lookup"><span data-stu-id="9ec11-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="9ec11-127">在 **方案總管**，以滑鼠右鍵按一下方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9ec11-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="9ec11-128">在 **通用屬性**，選取**啟始專案**，然後按一下**單一啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="9ec11-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="9ec11-129">從**單一啟始專案**下拉式清單中，選取**用戶端**。</span><span class="sxs-lookup"><span data-stu-id="9ec11-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="9ec11-130">按一下 **確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9ec11-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="9ec11-131">若要建置範例，請按下 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="9ec11-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="9ec11-132">若要執行用戶端，請按下 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="9ec11-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ec11-133">如果這些步驟沒有作用，請確定，您的環境已正確設定，使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="9ec11-133">If these steps do not work, make sure that your environment has been properly set up, using the following steps:</span></span>  
>   
> 1.  <span data-ttu-id="9ec11-134">請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec11-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="9ec11-135">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec11-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="9ec11-136">若要執行單一或多個電腦組態中的範例，請遵循中的指示[執行 Windows Communication Foundation 範例](running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec11-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ec11-137">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9ec11-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9ec11-138">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9ec11-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ec11-139">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="9ec11-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ec11-140">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9ec11-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="9ec11-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ec11-141">See Also</span></span>  
 [<span data-ttu-id="9ec11-142">AppFabric 管理範例</span><span class="sxs-lookup"><span data-stu-id="9ec11-142">AppFabric Management Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193960)
