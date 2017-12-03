---
title: "階層式組態模型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28dcc698-226c-4b77-9e51-8bf45a36216c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcef9ebe1b4876e429da97b3e217dd32286e4d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="hierarchical-configuration-model"></a><span data-ttu-id="b3129-102">階層式組態模型</span><span class="sxs-lookup"><span data-stu-id="b3129-102">Hierarchical Configuration Model</span></span>
<span data-ttu-id="b3129-103">此範例示範如何針對服務實作組態檔的階層。</span><span class="sxs-lookup"><span data-stu-id="b3129-103">This sample demonstrates how to implement a hierarchy of configuration files for services.</span></span> <span data-ttu-id="b3129-104">它也會示範如何從階層中較高的層級繼承繫結、服務行為與端點行為。</span><span class="sxs-lookup"><span data-stu-id="b3129-104">It also shows how bindings, service behaviors, and endpoint behaviors are inherited from higher levels in the hierarchy.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="b3129-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="b3129-105">Sample details</span></span>  
 <span data-ttu-id="b3129-106">針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 開發之其中一個功能是階層組態模型中的改進功能。</span><span class="sxs-lookup"><span data-stu-id="b3129-106">One of the features developed for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] is the improvement in the hierarchical configuration model.</span></span> <span data-ttu-id="b3129-107">階層組態模型的範例是由 Machine.config -> Rootweb.config -> Web.config 所定義的範例。在 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] 中，於組態階層之較上層中定義的那些繫結與行為都會在沒有明確組態的情況下，加入至您的服務。</span><span class="sxs-lookup"><span data-stu-id="b3129-107">An example of a hierarchical configuration model would be the one defined by Machine.config -> Rootweb.config -> Web.config. In [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], those bindings and behaviors that are defined in upper levels in the configuration hierarchy are added to your services with no explicit configuration.</span></span> <span data-ttu-id="b3129-108">此範例示範如何能夠透過依賴在電腦或應用程式層級定義的組態項目，簡化您的服務組態。</span><span class="sxs-lookup"><span data-stu-id="b3129-108">This sample shows how it is possible to simplify your service configuration by relying on configuration elements defined at the computer or the application level.</span></span>  
  
 <span data-ttu-id="b3129-109">這個範例由三個階層層級中定義的九個服務所組成。</span><span class="sxs-lookup"><span data-stu-id="b3129-109">This sample consists of nine services, defined in three levels of hierarchy.</span></span> <span data-ttu-id="b3129-110">`Service1` 位於根目錄。</span><span class="sxs-lookup"><span data-stu-id="b3129-110">`Service1` is at the root.</span></span> <span data-ttu-id="b3129-111">`Service2` 和 `Service3` 從 `Service1` 繼承預設元素。</span><span class="sxs-lookup"><span data-stu-id="b3129-111">`Service2` and `Service3` inherit the default elements from `Service1`.</span></span> <span data-ttu-id="b3129-112">`Service4`、`Service5`、`Service6` 和 `Service7` 是在階層的第三個層級定義的，且從 `Service3` 繼承預設項目。</span><span class="sxs-lookup"><span data-stu-id="b3129-112">`Service4`, `Service5`, `Service6` and `Service7` are defined at a third level of the hierarchy, inheriting the default elements from `Service3`.</span></span> <span data-ttu-id="b3129-113">最後，`Service10` 和 `Service11` 則位於階層的第四個層級。</span><span class="sxs-lookup"><span data-stu-id="b3129-113">Finally `Service10` and `Service11` are at a fourth level of the hierarchy.</span></span>  
  
 <span data-ttu-id="b3129-114">所有服務都會實作 `IDesc` 合約。</span><span class="sxs-lookup"><span data-stu-id="b3129-114">All the services implement the `IDesc` contract.</span></span> <span data-ttu-id="b3129-115">以下是 `IDesc` 介面的定義，這個定義會顯示在此介面中公開的方法。</span><span class="sxs-lookup"><span data-stu-id="b3129-115">The following is the definition of the `IDesc` interface that shows the methods exposed in this interface.</span></span> <span data-ttu-id="b3129-116">`IDesc` 介面是在 Service1.cs 中定義的。</span><span class="sxs-lookup"><span data-stu-id="b3129-116">The `IDesc` interface is defined in Service1.cs.</span></span>  
  
```  
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
  
 <span data-ttu-id="b3129-117">由服務針對這些方法進行的實作相當直接。</span><span class="sxs-lookup"><span data-stu-id="b3129-117">The implementation of these methods by the services is straightforward.</span></span> <span data-ttu-id="b3129-118">`ListEndpoints` 會逐一查看所有服務端點，並傳回服務所擁有之所有端點的清單。</span><span class="sxs-lookup"><span data-stu-id="b3129-118">`ListEndpoints` iterates through all the service endpoints and returns a list of all the endpoints that the service has.</span></span> <span data-ttu-id="b3129-119">`ListServiceBehaviors` 會逐一查看加入至服務的所有行為，並傳回與服務相關聯之所有服務行為的清單。</span><span class="sxs-lookup"><span data-stu-id="b3129-119">`ListServiceBehaviors` iterates through all the behaviors added to the service and returns the list of all the service behaviors associated with the service.</span></span> <span data-ttu-id="b3129-120">`ListEndpointBehaviors` 以類似於 `ListServiceBehaviors` 的方式運作，但它會傳回端點行為的清單。</span><span class="sxs-lookup"><span data-stu-id="b3129-120">`ListEndpointBehaviors` behaves in a similar way to `ListServiceBehaviors`, but it returns the list of endpoint behaviors instead.</span></span>  
  
 <span data-ttu-id="b3129-121">這個實作可讓用戶端了解服務公開多少端點，以及哪些服務行為和端點行為已加入至服務。</span><span class="sxs-lookup"><span data-stu-id="b3129-121">This implementation allows the client to know how many endpoints the service is exposing and which service behaviors and endpoint behaviors have been added to the service.</span></span> <span data-ttu-id="b3129-122">已經當做範例一部分實作的用戶端會將服務參考加入至方案中的所有服務，並針對每個服務顯示這些項目。</span><span class="sxs-lookup"><span data-stu-id="b3129-122">The client that has been implemented as part of the sample adds a service reference to all the services in the solution and shows these elements for each one of the services.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="b3129-123">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="b3129-123">To use this sample</span></span>  
  
#### <a name="to-run-the-client"></a><span data-ttu-id="b3129-124">若要執行用戶端</span><span class="sxs-lookup"><span data-stu-id="b3129-124">To run the client</span></span>  
  
1.  <span data-ttu-id="b3129-125">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 ConfigHierarchicalModel.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="b3129-125">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the ConfigHierarchicalModel.sln file.</span></span>  
  
2.  <span data-ttu-id="b3129-126">如果用戶端專案還未設定為啟始專案，請遵循下列步驟進行。</span><span class="sxs-lookup"><span data-stu-id="b3129-126">The client project is not already set up as the start-up project, follow these steps.</span></span>  
  
    1.  <span data-ttu-id="b3129-127">在**方案總管 中**，以滑鼠右鍵按一下方案，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b3129-127">In **Solution Explorer**, right-click the solution and then select **Properties**.</span></span>  
  
    2.  <span data-ttu-id="b3129-128">在**通用屬性**，選取**啟始專案**，然後按一下 **單一啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="b3129-128">In **Common Properties**, select **Startup Project**, and then click **Single startup project**.</span></span>  
  
    3.  <span data-ttu-id="b3129-129">從**單一啟始專案**下拉式清單中，選取**用戶端**。</span><span class="sxs-lookup"><span data-stu-id="b3129-129">From the **Single startup project** drop-down, select **Client**.</span></span>  
  
    4.  <span data-ttu-id="b3129-130">按一下**確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b3129-130">Click **OK** to close the dialog.</span></span>  
  
3.  <span data-ttu-id="b3129-131">若要建置範例，請按下 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="b3129-131">To build the sample, press CTRL+SHIFT+B.</span></span>  
  
4.  <span data-ttu-id="b3129-132">若要執行用戶端，請按下 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="b3129-132">To run the client, press Ctrl+F5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3129-133">如果這些步驟沒有作用，則請使用下列步驟確認您的環境已正確設定。</span><span class="sxs-lookup"><span data-stu-id="b3129-133">If these steps do not work, then make sure that your environment has been properly set up, using the following steps.</span></span>  
>   
>  1.  <span data-ttu-id="b3129-134">請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b3129-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
> 2.  <span data-ttu-id="b3129-135">若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b3129-135">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
> 3.  <span data-ttu-id="b3129-136">若要執行範例單一或多個電腦組態，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="b3129-136">To run the sample in a single or multiple computer configurations, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3129-137">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b3129-137">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b3129-138">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b3129-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3129-139">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="b3129-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3129-140">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b3129-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigHierarchicalModel`  
  
## <a name="see-also"></a><span data-ttu-id="b3129-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3129-141">See Also</span></span>  
 [<span data-ttu-id="b3129-142">AppFabric 管理範例</span><span class="sxs-lookup"><span data-stu-id="b3129-142">AppFabric Management Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193960)
