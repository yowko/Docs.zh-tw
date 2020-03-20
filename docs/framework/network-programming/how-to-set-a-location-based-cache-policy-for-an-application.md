---
title: 如何：為應用程式設定以位置為基礎的快取原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180772"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="a3f1f-102">如何：為應用程式設定以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="a3f1f-103">以位置為基礎的快取原則，可讓應用程式明確地定義根據所要求資源位置的快取行為。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="a3f1f-104">本主題將示範如何以程式設計方式設定快取原則。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="a3f1f-105">有關使用設定檔為應用程式設定策略的資訊，請參閱[\<請求緩存>元素（網路設置）。](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a3f1f-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="a3f1f-106">為應用程式設定以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="a3f1f-107">建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="a3f1f-108">設定原則物件作為應用程式定義域的預設值。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="a3f1f-109">設定從快取中取得所要求資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="a3f1f-110">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> 來建立下列原則：從快取中取得可用的所要求資源，否則將要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="a3f1f-111">用戶端與伺服器之間的任何快取都可以滿足要求，包括遠端快取。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="a3f1f-112">設定防止任何快取提供資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="a3f1f-113">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> 來建立下列原則：防止任何快取提供所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="a3f1f-114">此原則層級會從本機快取中移除存在的資源，並且向遠端快取指出它們也應該移除資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="a3f1f-115">設定唯有所要求的資源位於本機快取中時，才會傳回這些資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="a3f1f-116">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> 來建立下列原則：唯有所要求的資源位於本機快取中時，才會傳回這些資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="a3f1f-117">如果所要求的資源不在快取中，則會擲回 <xref:System.Net.WebException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="a3f1f-118">設定防止本機快取提供資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="a3f1f-119">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> 來建立下列原則：防止本機快取提供所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="a3f1f-120">如果所要求的資源位於中繼快取中，而且已成功重新驗證，則中繼快取可以提供所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="a3f1f-121">設定防止任何快取提供所要求資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="a3f1f-122">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> 來建立下列原則：防止任何快取提供所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="a3f1f-123">伺服器傳回的資源可以儲存在快取中。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="a3f1f-124">設定伺服器上的資源並未比快取複本更新時，可讓任何快取提供所要求資源的原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="a3f1f-125">藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> 來建立下列原則：伺服器上的資源並未比快取複本更新時，可讓任何快取提供所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="a3f1f-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a3f1f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f1f-126">See also</span></span>

- [<span data-ttu-id="a3f1f-127">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="a3f1f-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="a3f1f-128">緩存策略</span><span class="sxs-lookup"><span data-stu-id="a3f1f-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="a3f1f-129">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="a3f1f-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="a3f1f-130">Time-Based Cache Policies</span><span class="sxs-lookup"><span data-stu-id="a3f1f-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="a3f1f-131">\<請求緩存>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="a3f1f-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
