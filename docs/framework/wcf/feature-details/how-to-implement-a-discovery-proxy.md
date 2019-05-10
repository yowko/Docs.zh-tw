---
title: HOW TO：實作探索 Proxy
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: 0928db476c759ac76a117485586d43c2414e2945
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635281"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="b49c8-102">HOW TO：實作探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="b49c8-102">How to: Implement a Discovery Proxy</span></span>
<span data-ttu-id="b49c8-103">本主題說明如何實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b49c8-103">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="b49c8-104">如需 Windows Communication Foundation (WCF) 中的 [探索] 功能的詳細資訊，請參閱[WCF 探索概觀](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b49c8-104">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md).</span></span> <span data-ttu-id="b49c8-105">探索 Proxy 可透過建立延伸類別的方式來實作，該類別可擴充<xref:System.ServiceModel.Discovery.DiscoveryProxy> 抽象類別。</span><span class="sxs-lookup"><span data-stu-id="b49c8-105">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="b49c8-106">許多其他支援類別都已在此範例中定義和使用。</span><span class="sxs-lookup"><span data-stu-id="b49c8-106">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="b49c8-107">`OnResolveAsyncResult`、`OnFindAsyncResult` 和 `AsyncResult`。</span><span class="sxs-lookup"><span data-stu-id="b49c8-107">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="b49c8-108">這些類別會實作 <xref:System.IAsyncResult> 介面。</span><span class="sxs-lookup"><span data-stu-id="b49c8-108">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="b49c8-109">如需詳細資訊<xref:System.IAsyncResult>請參閱 < [System.IAsyncResult 介面](xref:System.IAsyncResult)。</span><span class="sxs-lookup"><span data-stu-id="b49c8-109">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="b49c8-110">本主題將實作探索 Proxy 分為三個主要部分：</span><span class="sxs-lookup"><span data-stu-id="b49c8-110">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="b49c8-111">定義類別，包含資料存放區並可擴充抽象 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 類別。</span><span class="sxs-lookup"><span data-stu-id="b49c8-111">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="b49c8-112">實作 Helper `AsyncResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="b49c8-112">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="b49c8-113">裝載探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b49c8-113">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="b49c8-114">若要建立新的主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="b49c8-114">To create a new console application project</span></span>

1. <span data-ttu-id="b49c8-115">啟動 Visual Studio 2012。</span><span class="sxs-lookup"><span data-stu-id="b49c8-115">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="b49c8-116">建立新的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b49c8-116">Create a new console application project.</span></span> <span data-ttu-id="b49c8-117">將專案命名為 `DiscoveryProxy`，並將方案命名為 `DiscoveryProxyExample`。</span><span class="sxs-lookup"><span data-stu-id="b49c8-117">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="b49c8-118">將下列參考加入至專案中</span><span class="sxs-lookup"><span data-stu-id="b49c8-118">Add the following references to the project</span></span>

    1. <span data-ttu-id="b49c8-119">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="b49c8-119">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="b49c8-120">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="b49c8-120">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    >  <span data-ttu-id="b49c8-121">確定您參考的組件為 4.0 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b49c8-121">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="b49c8-122">若要實作 ProxyDiscoveryService 類別</span><span class="sxs-lookup"><span data-stu-id="b49c8-122">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="b49c8-123">將新的程式碼檔案加入至專案，並將其命名為 DiscoveryProxy.cs。</span><span class="sxs-lookup"><span data-stu-id="b49c8-123">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="b49c8-124">將下列 `using` 陳述式加入至 DiscoveryProxy.cs。</span><span class="sxs-lookup"><span data-stu-id="b49c8-124">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="b49c8-125">從 `DiscoveryProxyService` 衍生 <xref:System.ServiceModel.Discovery.DiscoveryProxy>。</span><span class="sxs-lookup"><span data-stu-id="b49c8-125">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="b49c8-126">將 `ServiceBehavior` 屬性套用至類別，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="b49c8-126">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="b49c8-127">在 `DiscoveryProxy` 類別內定義字典以保存已註冊的服務。</span><span class="sxs-lookup"><span data-stu-id="b49c8-127">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="b49c8-128">定義初始化字典的建構函式。</span><span class="sxs-lookup"><span data-stu-id="b49c8-128">Define a constructor that initializes the dictionary.</span></span>

    ```
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="b49c8-129">若要定義用來更新探索 Proxy 快取的方法</span><span class="sxs-lookup"><span data-stu-id="b49c8-129">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="b49c8-130">實作 `AddOnlineservice` 方法，將服務加入至快取。</span><span class="sxs-lookup"><span data-stu-id="b49c8-130">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="b49c8-131">Proxy 每次收到公告訊息時都會呼叫此動作。</span><span class="sxs-lookup"><span data-stu-id="b49c8-131">This is called every time the proxy receives an announcement message.</span></span>

    ```
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
            }
    ```

2. <span data-ttu-id="b49c8-132">實作 `RemoveOnlineService` 方法，這個方法可用來移除來自快取的服務。</span><span class="sxs-lookup"><span data-stu-id="b49c8-132">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
            {
                if (endpointDiscoveryMetadata != null)
                {
                    lock (this.onlineServices)
                    {
                        this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                    }

                    PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
                }
            }
    ```

3. <span data-ttu-id="b49c8-133">實作 `MatchFromOnlineService` 方法，這些方法會嘗試比對某個服務與字典中的服務。</span><span class="sxs-lookup"><span data-stu-id="b49c8-133">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```
    void MatchFromOnlineService(FindRequestContext findRequestContext)
            {
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                        {
                            findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                        }
                    }
                }
            }
    ```

    ```
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
            {
                EndpointDiscoveryMetadata matchingEndpoint = null;
                lock (this.onlineServices)
                {
                    foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                    {
                        if (criteria.Address == endpointDiscoveryMetadata.Address)
                        {
                            matchingEndpoint = endpointDiscoveryMetadata;
                        }
                    }
                }
                return matchingEndpoint;
            }
    ```

4. <span data-ttu-id="b49c8-134">實作 `PrintDiscoveryMetadata` 方法，這個方法可提供使用者探索 Proxy 進行中的主控台文字輸出。</span><span class="sxs-lookup"><span data-stu-id="b49c8-134">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
            {
                Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
                foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
                {
                    Console.WriteLine("** " + contractName.ToString());
                    break;
                }
                Console.WriteLine("**** Operation Completed");
            }
    ```

5. <span data-ttu-id="b49c8-135">將下列 AsyncResult 類別加入至 DiscoveryProxyService。</span><span class="sxs-lookup"><span data-stu-id="b49c8-135">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="b49c8-136">這些類別用於區分不同的非同步作業結果。</span><span class="sxs-lookup"><span data-stu-id="b49c8-136">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
            {
                public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
            {
                public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
                }
            }

            sealed class OnFindAsyncResult : AsyncResult
            {
                public OnFindAsyncResult(AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.Complete(true);
                }

                public static void End(IAsyncResult result)
                {
                    AsyncResult.End<OnFindAsyncResult>(result);
                }
            }

            sealed class OnResolveAsyncResult : AsyncResult
            {
                EndpointDiscoveryMetadata matchingEndpoint;

                public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                    : base(callback, state)
                {
                    this.matchingEndpoint = matchingEndpoint;
                    this.Complete(true);
                }

                public static EndpointDiscoveryMetadata End(IAsyncResult result)
                {
                    OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                    return thisPtr.matchingEndpoint;
                }
            }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="b49c8-137">若要定義可實作探索 Proxy 功能的方法</span><span class="sxs-lookup"><span data-stu-id="b49c8-137">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="b49c8-138">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-138">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-139">當探索 Proxy 收到線上公告訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-139">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
            protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.AddOnlineService(endpointDiscoveryMetadata);
                return new OnOnlineAnnouncementAsyncResult(callback, state);
            }
    ```

2. <span data-ttu-id="b49c8-140">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-140">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-141">當探索 Proxy 完成處理公告訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-141">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
            {
                OnOnlineAnnouncementAsyncResult.End(result);
            }
    ```

3. <span data-ttu-id="b49c8-142">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-142">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-143">當探索 Proxy 收到離線公告訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-143">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
            protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
            {
                this.RemoveOnlineService(endpointDiscoveryMetadata);
                return new OnOfflineAnnouncementAsyncResult(callback, state);
            }
    ```

4. <span data-ttu-id="b49c8-144">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-144">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-145">當探索 Proxy 完成處理離線公告訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-145">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
            {
                OnOfflineAnnouncementAsyncResult.End(result);
            }
    ```

5. <span data-ttu-id="b49c8-146">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-146">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-147">當探索 Proxy 收到尋找要求時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-147">This method is called when the discovery proxy receives a find request.</span></span>

    ```
    // OnBeginFind method is called when a Probe request message is received by the Proxy
            protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
            {
                this.MatchFromOnlineService(findRequestContext);
                return new OnFindAsyncResult(callback, state);
            }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="b49c8-148">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-148">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-149">當探索 Proxy 完成處理尋找要求時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-149">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```
    protected override void OnEndFind(IAsyncResult result)
            {
                OnFindAsyncResult.End(result);
            }
    ```

7. <span data-ttu-id="b49c8-150">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-150">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-151">當探索 Proxy 收到解析訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-151">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
            protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
            {
                return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
            }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="b49c8-152">覆寫 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-152">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b49c8-153">當探索 Proxy 完成處理解析訊息時，就會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b49c8-153">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

 <span data-ttu-id="b49c8-154">OnBegin.</span><span class="sxs-lookup"><span data-stu-id="b49c8-154">The OnBegin..</span></span> <span data-ttu-id="b49c8-155">/ OnEnd.</span><span class="sxs-lookup"><span data-stu-id="b49c8-155">/ OnEnd..</span></span> <span data-ttu-id="b49c8-156">方法提供後續探索作業的邏輯。</span><span class="sxs-lookup"><span data-stu-id="b49c8-156">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="b49c8-157">例如，<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> 和 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> 方法可實作探索 Proxy 的尋找邏輯。</span><span class="sxs-lookup"><span data-stu-id="b49c8-157">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="b49c8-158">當探索 Proxy 收到檢測訊息時，便會執行這些方法來傳送回應至用戶端。</span><span class="sxs-lookup"><span data-stu-id="b49c8-158">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="b49c8-159">您可以修改尋找邏輯，例如，您可透過演算法或應用程式特定 XML 中繼資料剖析的方式，加入自訂範圍比對，做為尋找作業的一部分。</span><span class="sxs-lookup"><span data-stu-id="b49c8-159">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="b49c8-160">若要實作 AsyncResult 類別</span><span class="sxs-lookup"><span data-stu-id="b49c8-160">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="b49c8-161">定義抽象基底類別 AsyncResult，這個類別用於衍生各種非同步結果類別。</span><span class="sxs-lookup"><span data-stu-id="b49c8-161">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="b49c8-162">建立名為 AsyncResult.cs 的新程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="b49c8-162">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="b49c8-163">將下列 `using` 陳述式加入至 AsyncResult.cs。</span><span class="sxs-lookup"><span data-stu-id="b49c8-163">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="b49c8-164">加入下列 AsyncResult 類別。</span><span class="sxs-lookup"><span data-stu-id="b49c8-164">Add the following AsyncResult class.</span></span>

    ```
    abstract class AsyncResult : IAsyncResult
        {
            AsyncCallback callback;
            bool completedSynchronously;
            bool endCalled;
            Exception exception;
            bool isCompleted;
            ManualResetEvent manualResetEvent;
            object state;
            object thisLock;

            protected AsyncResult(AsyncCallback callback, object state)
            {
                this.callback = callback;
                this.state = state;
                this.thisLock = new object();
            }

            public object AsyncState
            {
                get
                {
                    return state;
                }
            }

            public WaitHandle AsyncWaitHandle
            {
                get
                {
                    if (manualResetEvent != null)
                    {
                        return manualResetEvent;
                    }
                    lock (ThisLock)
                    {
                        if (manualResetEvent == null)
                        {
                            manualResetEvent = new ManualResetEvent(isCompleted);
                        }
                    }
                    return manualResetEvent;
                }
            }

            public bool CompletedSynchronously
            {
                get
                {
                    return completedSynchronously;
                }
            }

            public bool IsCompleted
            {
                get
                {
                    return isCompleted;
                }
            }

            object ThisLock
            {
                get
                {
                    return this.thisLock;
                }
            }

            protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
                where TAsyncResult : AsyncResult
            {
                if (result == null)
                {
                    throw new ArgumentNullException("result");
                }

                TAsyncResult asyncResult = result as TAsyncResult;

                if (asyncResult == null)
                {
                    throw new ArgumentException("Invalid async result.", "result");
                }

                if (asyncResult.endCalled)
                {
                    throw new InvalidOperationException("Async object already ended.");
                }

                asyncResult.endCalled = true;

                if (!asyncResult.isCompleted)
                {
                    asyncResult.AsyncWaitHandle.WaitOne();
                }

                if (asyncResult.manualResetEvent != null)
                {
                    asyncResult.manualResetEvent.Close();
                }

                if (asyncResult.exception != null)
                {
                    throw asyncResult.exception;
                }

                return asyncResult;
            }

            protected void Complete(bool completedSynchronously)
            {
                if (isCompleted)
                {
                    throw new InvalidOperationException("This async result is already completed.");
                }

                this.completedSynchronously = completedSynchronously;

                if (completedSynchronously)
                {
                    this.isCompleted = true;
                }
                else
                {
                    lock (ThisLock)
                    {
                        this.isCompleted = true;
                        if (this.manualResetEvent != null)
                        {
                            this.manualResetEvent.Set();
                        }
                    }
                }

                if (callback != null)
                {
                    callback(this);
                }
            }

            protected void Complete(bool completedSynchronously, Exception exception)
            {
                this.exception = exception;
                Complete(completedSynchronously);
            }
        }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="b49c8-165">若要裝載 DiscoveryProxy</span><span class="sxs-lookup"><span data-stu-id="b49c8-165">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="b49c8-166">開啟 DiscoveryProxyExample 專案中的 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="b49c8-166">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="b49c8-167">加入下列 `using` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b49c8-167">Add the following `using` statements.</span></span>

    ```
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="b49c8-168">在 `Main()` 方法中，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b49c8-168">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="b49c8-169">這樣做可建立 `DiscoveryProxy` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b49c8-169">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
                Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

                // Host the DiscoveryProxy service
                ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="b49c8-170">接著，加入下列程式碼以加入探索端點與公告端點。</span><span class="sxs-lookup"><span data-stu-id="b49c8-170">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```
    try
              {
                  // Add DiscoveryEndpoint to receive Probe and Resolve messages
                  DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                  discoveryEndpoint.IsSystemEndpoint = false;

                  // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                  AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                  proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                  proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                  proxyServiceHost.Open();

                  Console.WriteLine("Proxy Service started.");
                  Console.WriteLine();
                  Console.WriteLine("Press <ENTER> to terminate the service.");
                  Console.WriteLine();
                  Console.ReadLine();

                  proxyServiceHost.Close();
              }
              catch (CommunicationException e)
              {
                  Console.WriteLine(e.Message);
              }
              catch (TimeoutException e)
              {
                  Console.WriteLine(e.Message);
              }

              if (proxyServiceHost.State != CommunicationState.Closed)
              {
                  Console.WriteLine("Aborting the service...");
                  proxyServiceHost.Abort();
              }
    ```

 <span data-ttu-id="b49c8-171">您已經完成實作探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="b49c8-171">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="b49c8-172">繼續前往[How to:實作以探索 Proxy 註冊的可探索服務](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="b49c8-172">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="b49c8-173">範例</span><span class="sxs-lookup"><span data-stu-id="b49c8-173">Example</span></span>
 <span data-ttu-id="b49c8-174">以下是本主題所使用之程式碼的完整清單。</span><span class="sxs-lookup"><span data-stu-id="b49c8-174">This is the full listing of the code used in this topic.</span></span>

```
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    if (manualResetEvent == null)
                    {
                        manualResetEvent = new ManualResetEvent(isCompleted);
                    }
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b49c8-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b49c8-175">See also</span></span>

- [<span data-ttu-id="b49c8-176">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="b49c8-176">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="b49c8-177">如何：實作以探索 Proxy 註冊的可探索服務</span><span class="sxs-lookup"><span data-stu-id="b49c8-177">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="b49c8-178">如何：實作使用探索 Proxy 尋找服務的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="b49c8-178">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="b49c8-179">如何：測試探索 Proxy</span><span class="sxs-lookup"><span data-stu-id="b49c8-179">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)
