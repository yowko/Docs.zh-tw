---
title: "變更傳送活動的快取共用層級"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d0254673277cf6435ec835351b89fc03db01b2ae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="9166b-102">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="9166b-102">Changing the Cache Sharing Levels for Send Activities</span></span>
<span data-ttu-id="9166b-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 擴充可讓您為使用 <xref:System.ServiceModel.Activities.Send> 傳訊活動傳送訊息至服務端點的工作流程自訂快取共用層級、通道處理站快取的設定，以及通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="9166b-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="9166b-104">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="9166b-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="9166b-105">通道處理站快取會包含快取的 <xref:System.ServiceModel.ChannelFactory%601> 物件。</span><span class="sxs-lookup"><span data-stu-id="9166b-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="9166b-106">通道快取則包含快取的通道。</span><span class="sxs-lookup"><span data-stu-id="9166b-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9166b-107">工作流程可以利用 <xref:System.ServiceModel.Activities.Send> 傳訊活動傳送訊息或參數。</span><span class="sxs-lookup"><span data-stu-id="9166b-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="9166b-108">工作流程執行階段會將通道處理站加入快取，這個快取會在您使用 <xref:System.ServiceModel.Channels.IRequestChannel> 活動搭配 <xref:System.ServiceModel.Activities.ReceiveReply> 活動時建立 <xref:System.ServiceModel.Activities.Send> 型別的通道，以及在您只使用 <xref:System.ServiceModel.Channels.IOutputChannel> 活動 (無 <xref:System.ServiceModel.Activities.Send>) 時建立 <xref:System.ServiceModel.Activities.ReceiveReply> 型別的通道。</span><span class="sxs-lookup"><span data-stu-id="9166b-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="9166b-109">快取共用層級</span><span class="sxs-lookup"><span data-stu-id="9166b-109">The Cache Sharing Levels</span></span>  
 <span data-ttu-id="9166b-110">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="9166b-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="9166b-111">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="9166b-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="9166b-112">此快取僅適用於 <xref:System.ServiceModel.Activities.Send> 活動 (此活動不使用組態中定義的端點，除非已啟用不安全的快取)。</span><span class="sxs-lookup"><span data-stu-id="9166b-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="9166b-113">以下是工作流程中的 <xref:System.ServiceModel.Activities.Send> 活動適用的不同快取共用層級，以及其建議用法：</span><span class="sxs-lookup"><span data-stu-id="9166b-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
-   <span data-ttu-id="9166b-114">**主機層級**： 在主機共用層級，快取是僅適用於裝載工作流程服務主機中的工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="9166b-115">整個處理序快取中的工作流程服務主機間也可以共用快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
-   <span data-ttu-id="9166b-116">**執行個體層級**： 共用層級的執行個體，在快取可在其存留期的特定工作流程執行個體，但快取不適用於其他工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
-   <span data-ttu-id="9166b-117">**無快取**： 快取預設關閉如果您有使用端點組態中定義的工作流程。</span><span class="sxs-lookup"><span data-stu-id="9166b-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="9166b-118">在此情況下，建議保持關閉快取，因為開啟快取可能不安全。</span><span class="sxs-lookup"><span data-stu-id="9166b-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="9166b-119">例如，如果每次傳送都需要不同的識別 (不同的認證或使用模擬)。</span><span class="sxs-lookup"><span data-stu-id="9166b-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="9166b-120">變更用戶端工作流程的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="9166b-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  
 <span data-ttu-id="9166b-121">若要在用戶端工作流程中設定快取共用，請將 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的執行個體做為擴充，加入所需的一組工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="9166b-122">這樣會跨所有工作流程執行個體共用快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="9166b-123">下列程式碼範例示範如何執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9166b-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="9166b-124">首先，宣告 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="9166b-125">接下來，將快取擴充加入每個用戶端工作流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="9166b-126">變更裝載之工作流程服務的快取共用層級。</span><span class="sxs-lookup"><span data-stu-id="9166b-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  
 <span data-ttu-id="9166b-127">若要在裝載的工作流程服務中設定快取共用，請將 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的執行個體加入至所有工作流程服務主機做為擴充。</span><span class="sxs-lookup"><span data-stu-id="9166b-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="9166b-128">這樣會跨所有工作流程服務主機共用快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="9166b-129">下列程式碼範例示範如何執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9166b-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="9166b-130">首先，在類別層級宣告 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="9166b-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="9166b-131">接下來，將靜態快取擴充加入每個工作流程服務主機。</span><span class="sxs-lookup"><span data-stu-id="9166b-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="9166b-132">若要在裝載的工作流程服務中將快取共用設定至執行個體層級，請將 `Func<SendMessageChannelCache>` 委派加入至工作流程服務主機做為擴充，並且將這個委派指派至執行個體化 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的新執行個體的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9166b-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="9166b-133">這樣會讓每個個別工作流程執行個體產生不同的快取，而不是工作流程服務主機中的所有工作流程執行個體共用單一快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="9166b-134">下列程式碼範例示範如何使用 Lambda 運算式直接定義委派所指向的 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 擴充，以達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="9166b-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```  
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings   
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings   
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="9166b-135">自訂快取設定</span><span class="sxs-lookup"><span data-stu-id="9166b-135">Customizing Cache Settings</span></span>  
 <span data-ttu-id="9166b-136">您可以自訂通道處理站快取與通道快取的快取設定。</span><span class="sxs-lookup"><span data-stu-id="9166b-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="9166b-137">快取設定是在 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 類別中所定義的。</span><span class="sxs-lookup"><span data-stu-id="9166b-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="9166b-138"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別會定義在其預設的建構函式中之通道處理站快取與通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="9166b-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its default constructor.</span></span> <span data-ttu-id="9166b-139">下表列出這些屬於每個快取型別之快取設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="9166b-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="9166b-140">設定</span><span class="sxs-lookup"><span data-stu-id="9166b-140">Settings</span></span>|<span data-ttu-id="9166b-141">LeaseTimeout (分鐘)</span><span class="sxs-lookup"><span data-stu-id="9166b-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="9166b-142">IdleTimeout (分鐘)</span><span class="sxs-lookup"><span data-stu-id="9166b-142">IdleTimeout (min)</span></span>|<span data-ttu-id="9166b-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="9166b-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="9166b-144">處理站快取預設值</span><span class="sxs-lookup"><span data-stu-id="9166b-144">Factory Cache Default</span></span>|<span data-ttu-id="9166b-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="9166b-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="9166b-146">2</span><span class="sxs-lookup"><span data-stu-id="9166b-146">2</span></span>|<span data-ttu-id="9166b-147">16</span><span class="sxs-lookup"><span data-stu-id="9166b-147">16</span></span>|  
|<span data-ttu-id="9166b-148">通道快取預設值</span><span class="sxs-lookup"><span data-stu-id="9166b-148">Channel Cache Default</span></span>|<span data-ttu-id="9166b-149">5</span><span class="sxs-lookup"><span data-stu-id="9166b-149">5</span></span>|<span data-ttu-id="9166b-150">2</span><span class="sxs-lookup"><span data-stu-id="9166b-150">2</span></span>|<span data-ttu-id="9166b-151">16</span><span class="sxs-lookup"><span data-stu-id="9166b-151">16</span></span>|  
  
 <span data-ttu-id="9166b-152">若要自訂處理站快取與通道快取設定，請使用參數化的建構函式 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 將 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 類別執行具現化，並且將 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 的新執行個體 (具有自訂值)，傳遞至每個 `factorySettings` 和 `channelSettings` 參數。</span><span class="sxs-lookup"><span data-stu-id="9166b-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="9166b-153">接著，請將這個類別的新執行個體加入工作流程服務主機或工作流程執行個體，做為擴充。</span><span class="sxs-lookup"><span data-stu-id="9166b-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="9166b-154">下列程式碼範例示範如何針對工作流程執行個體執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="9166b-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(5),   
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="9166b-155">當您的工作流程服務中具有在組態中定義的端點時，若要啟用快取，請使用參數化建構函式 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 執行具現化 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 類別 (`allowUnsafeCaching` 參數設定為 `true`)。</span><span class="sxs-lookup"><span data-stu-id="9166b-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="9166b-156">接著，請將這個類別的新執行個體加入工作流程服務主機或工作流程執行個體，做為擴充。</span><span class="sxs-lookup"><span data-stu-id="9166b-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="9166b-157">下列程式碼範例示範如何啟用工作流程執行個體的快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="9166b-158">若要完全停用通道處理站與通道的快取，請停用通道處理站快取。</span><span class="sxs-lookup"><span data-stu-id="9166b-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="9166b-159">這麼做也會關閉通道快取，因為通道的擁有者是與其對應的通道處理站。</span><span class="sxs-lookup"><span data-stu-id="9166b-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="9166b-160">若要停用通道處理站快取，請將 `factorySettings` 參數傳送至 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 建構函式，這個建構函式已經初始化為 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 執行個體，其 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 的值為 0。</span><span class="sxs-lookup"><span data-stu-id="9166b-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="9166b-161">下列程式碼範例會顯示這點。</span><span class="sxs-lookup"><span data-stu-id="9166b-161">The following code example shows this.</span></span>  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="9166b-162">您可以選擇只使用通道處理站快取並停用通道快取，方法是將 `channelSettings` 參數傳送至 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 建構函式，這個建構函式已初始化為 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 執行個體，其 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 值為 0。</span><span class="sxs-lookup"><span data-stu-id="9166b-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="9166b-163">下列程式碼範例會顯示這點。</span><span class="sxs-lookup"><span data-stu-id="9166b-163">The following code example shows this.</span></span>  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="9166b-164">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="9166b-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="9166b-165">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="9166b-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="9166b-166">下列範例顯示組態檔中包含的內容`MyChannelCacheBehavior`使用自訂處理站快取和通道快取設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="9166b-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="9166b-167">這個服務行為加入至服務，透過`behaviorConfiguarion`屬性。</span><span class="sxs-lookup"><span data-stu-id="9166b-167">This service behavior is added to the service through the `behaviorConfiguarion` attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
