---
title: 自訂尋找準則
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 699260fcef7680710f721d213dbf1126ebf7a896
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135391"
---
# <a name="custom-find-criteria"></a><span data-ttu-id="a80f5-102">自訂尋找準則</span><span class="sxs-lookup"><span data-stu-id="a80f5-102">Custom Find Criteria</span></span>
<span data-ttu-id="a80f5-103">此範例示範如何使用邏輯建立自訂範圍比對，以及如何實作自訂探索服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="a80f5-104">用戶端使用自訂範圍比對功能來精簡並進一步建立在 WCF 探索之系統提供的尋找功能之上。</span><span class="sxs-lookup"><span data-stu-id="a80f5-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="a80f5-105">此範例包含的案例如下：</span><span class="sxs-lookup"><span data-stu-id="a80f5-105">The scenario this sample covers is as follows:</span></span>  
  
1.  <span data-ttu-id="a80f5-106">用戶端要尋找計算機服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-106">A client is looking for a calculator service.</span></span>  
  
2.  <span data-ttu-id="a80f5-107">若要精簡其搜尋範圍，用戶端必須使用自訂範圍比對規則。</span><span class="sxs-lookup"><span data-stu-id="a80f5-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3.  <span data-ttu-id="a80f5-108">根據這個規則，如果端點符合用戶端指定的任何範圍，服務就會向用戶端回應。</span><span class="sxs-lookup"><span data-stu-id="a80f5-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a80f5-109">示範</span><span class="sxs-lookup"><span data-stu-id="a80f5-109">Demonstrates</span></span>  
  
-   <span data-ttu-id="a80f5-110">建立自訂探索服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-110">Creating a custom discovery service.</span></span>  
  
-   <span data-ttu-id="a80f5-111">透過演算法實作自訂範圍比對。</span><span class="sxs-lookup"><span data-stu-id="a80f5-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a80f5-112">討論</span><span class="sxs-lookup"><span data-stu-id="a80f5-112">Discussion</span></span>  
 <span data-ttu-id="a80f5-113">用戶端會尋找"OR"類型比對準則。</span><span class="sxs-lookup"><span data-stu-id="a80f5-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="a80f5-114">如果端點上的範圍符合用戶端提供的任何範圍，服務就會回應。</span><span class="sxs-lookup"><span data-stu-id="a80f5-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="a80f5-115">在此情況下，用戶端會在下列清單中尋找擁有任何範圍的計算機服務：</span><span class="sxs-lookup"><span data-stu-id="a80f5-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1.  `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2.  `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3.  `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="a80f5-116">若要達成這個目的，用戶端會引導服務依照 URI 傳入自訂範圍比對來使用自訂範圍比對規則。</span><span class="sxs-lookup"><span data-stu-id="a80f5-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="a80f5-117">若要簡化自訂範圍比對，服務所使用的自訂探索服務必須了解自訂範圍比對並實作相關聯的比對邏輯。</span><span class="sxs-lookup"><span data-stu-id="a80f5-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="a80f5-118">開啟用戶端專案中的 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="a80f5-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="a80f5-119">請注意，`ScopeMatchBy` 物件的 `FindCriteria` 欄位會設定為特定的 URI。</span><span class="sxs-lookup"><span data-stu-id="a80f5-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="a80f5-120">此識別碼會傳送到服務中。</span><span class="sxs-lookup"><span data-stu-id="a80f5-120">This identifier is sent to the service.</span></span> <span data-ttu-id="a80f5-121">如果服務不了解這個規則，就會忽略用戶端的尋找要求。</span><span class="sxs-lookup"><span data-stu-id="a80f5-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="a80f5-122">開啟服務專案。</span><span class="sxs-lookup"><span data-stu-id="a80f5-122">Open the service project.</span></span> <span data-ttu-id="a80f5-123">實作自訂探索服務要使用三個檔案：</span><span class="sxs-lookup"><span data-stu-id="a80f5-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1.  <span data-ttu-id="a80f5-124">**AsyncResult.cs**： 這是實作`AsyncResult`所需的探索方法。</span><span class="sxs-lookup"><span data-stu-id="a80f5-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2.  <span data-ttu-id="a80f5-125">**CustomDiscoveryService.cs**： 這個檔案會實作自訂探索服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="a80f5-126">此實作會擴充 <xref:System.ServiceModel.Discovery.DiscoveryService> 類別並覆寫必要的方法。</span><span class="sxs-lookup"><span data-stu-id="a80f5-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="a80f5-127">請注意 <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> 方法的實作。</span><span class="sxs-lookup"><span data-stu-id="a80f5-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="a80f5-128">此方法會檢查用戶端是否依照規則指定自訂範圍比對。</span><span class="sxs-lookup"><span data-stu-id="a80f5-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="a80f5-129">這是用戶端先前指定的相同自訂 URI。</span><span class="sxs-lookup"><span data-stu-id="a80f5-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="a80f5-130">如果指定的自訂規則，則會遵循實作"OR"比對邏輯的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="a80f5-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="a80f5-131">這個自訂邏輯會通過服務所擁有之每個端點上的所有範圍。</span><span class="sxs-lookup"><span data-stu-id="a80f5-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="a80f5-132">如果有任何端點的範圍符合用戶端提供的任何範圍，探索服務會將該端點加入至傳回用戶端的回應中。</span><span class="sxs-lookup"><span data-stu-id="a80f5-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3.  <span data-ttu-id="a80f5-133">**CustomDiscoveryExtension.cs**： 實作探索服務的最後一個步驟是將這項實作自訂探索服務至服務主機。</span><span class="sxs-lookup"><span data-stu-id="a80f5-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="a80f5-134">此處所使用的協助程式類別為 `CustomDiscoveryExtension` 類別。</span><span class="sxs-lookup"><span data-stu-id="a80f5-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="a80f5-135">此類別會擴充 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> 類別。</span><span class="sxs-lookup"><span data-stu-id="a80f5-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="a80f5-136">使用者必須覆寫 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a80f5-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="a80f5-137">在此情況下，方法會傳回之前建立之自訂探索服務的執行個體。</span><span class="sxs-lookup"><span data-stu-id="a80f5-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="a80f5-138">`PublishedEndpoints` 是 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>，其中包含加入至 <xref:System.ServiceModel.ServiceHost> 的所有應用程式端點。</span><span class="sxs-lookup"><span data-stu-id="a80f5-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="a80f5-139">自訂探索服務使用這個端點填入其內部清單。</span><span class="sxs-lookup"><span data-stu-id="a80f5-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="a80f5-140">使用者也可以加入其他端點中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a80f5-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="a80f5-141">最後，開啟 Program.cs。</span><span class="sxs-lookup"><span data-stu-id="a80f5-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="a80f5-142">請注意，<xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 和 `CustomDiscoveryExtension` 都會加入至主機中。</span><span class="sxs-lookup"><span data-stu-id="a80f5-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="a80f5-143">一旦完成這個動作，而且主機所擁有的端點可用來接收探索訊息之後，應用程式就可以使用自訂探索服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="a80f5-144">請注意，用戶端不需知道位址，就能找到此服務。</span><span class="sxs-lookup"><span data-stu-id="a80f5-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a80f5-145">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="a80f5-145">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a80f5-146">開啟包含專案的方案。</span><span class="sxs-lookup"><span data-stu-id="a80f5-146">Open the solution that contains the project.</span></span>  
  
2.  <span data-ttu-id="a80f5-147">建置專案。</span><span class="sxs-lookup"><span data-stu-id="a80f5-147">Build the project.</span></span>  
  
3.  <span data-ttu-id="a80f5-148">執行服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="a80f5-148">Run the service application.</span></span>  
  
4.  <span data-ttu-id="a80f5-149">執行用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="a80f5-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a80f5-150">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a80f5-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a80f5-151">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a80f5-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a80f5-152">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="a80f5-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a80f5-153">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a80f5-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
