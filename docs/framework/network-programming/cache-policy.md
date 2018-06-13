---
title: 快取原則
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 36cf61982bb5a83e6031c35a19ba8ebf0b94aa6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393980"
---
# <a name="cache-policy"></a><span data-ttu-id="f494a-102">快取原則</span><span class="sxs-lookup"><span data-stu-id="f494a-102">Cache Policy</span></span>
<span data-ttu-id="f494a-103">快取原則所定義的規則用來判斷是否可以使用所要求資源的快取複本來滿足要求。</span><span class="sxs-lookup"><span data-stu-id="f494a-103">A cache policy defines rules that are used to determine whether a request can be satisfied using a cached copy of the requested resource.</span></span> <span data-ttu-id="f494a-104">應用程式指定有效期限的用戶端快取需求，但有效的快取原則是由用戶端快取需求、伺服器內容到期需求和伺服器重新驗證需求所決定。</span><span class="sxs-lookup"><span data-stu-id="f494a-104">Applications specify client cache requirements for freshness, but the effective cache policy is determined by the client cache requirements, the server's content expiration requirements, and the server's revalidation requirements.</span></span> <span data-ttu-id="f494a-105">用戶端快取原則與伺服器需求的互動一律會導致最保守的快取原則，協助確保將最新內容傳回給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="f494a-105">The interaction of client cache policy and server requirements always results in the most conservative cache policy, to help ensure that the freshest content is returned to the client application.</span></span>  
  
 <span data-ttu-id="f494a-106">快取原則是以位置為基礎或以時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="f494a-106">Cache policies are either location-based or time-based.</span></span> <span data-ttu-id="f494a-107">以位置為基礎的快取原則會根據所要求資源可以使用的位置，定義快取項目的有效期限。</span><span class="sxs-lookup"><span data-stu-id="f494a-107">A location-based cache policy defines the freshness of cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="f494a-108">以時間為基礎的快取原則會使用擷取資源的時間、與資源一起傳回的標頭，以及目前時間，定義快取項目的有效期限。</span><span class="sxs-lookup"><span data-stu-id="f494a-108">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, headers returned with the resource, and the current time.</span></span> <span data-ttu-id="f494a-109">大部分的應用程式可以使用以時間為基礎的預設快取原則，以實作可從 [http://www.ietf.org](http://www.ietf.org/) 取得之 RFC 2616 中所指定的快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-109">Most applications can use the default time-based cache policy, which implements the caching policy specified in RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/).</span></span>  
  
 <span data-ttu-id="f494a-110">下表中所述的類別是用來指定快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-110">The classes described in the following table are used to specify cache policies.</span></span>  
  
|<span data-ttu-id="f494a-111">類別名稱</span><span class="sxs-lookup"><span data-stu-id="f494a-111">Class name</span></span>|<span data-ttu-id="f494a-112">描述</span><span class="sxs-lookup"><span data-stu-id="f494a-112">Description</span></span>|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|<span data-ttu-id="f494a-113">針對使用 <xref:System.Net.HttpWebRequest> 物件所要求的資源，代表以位置為基礎和以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-113">Represents location-based and time-based cache policies for resources requested using <xref:System.Net.HttpWebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCachePolicy>|<span data-ttu-id="f494a-114">針對使用 <xref:System.Net.WebRequest> 物件所要求的資源，代表以位置為基礎的快取原則或以 <xref:System.Net.Cache.RequestCacheLevel.Default> 時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-114">Represents location-based cache policies or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based cache policy for resources requested using <xref:System.Net.WebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|<span data-ttu-id="f494a-115">指定值，用來建立以時間為基礎之 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-115">Specifies values used to create time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|<span data-ttu-id="f494a-116">指定值，用來建立以位置為基礎和以時間為基礎之 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-116">Specifies values used to create location-based and time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCacheLevel>|<span data-ttu-id="f494a-117">指定值，用來建立以位置為基礎或 <xref:System.Net.Cache.RequestCacheLevel.Default> 以時間為基礎的 <xref:System.Net.Cache.RequestCachePolicy> 物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-117">Specifies values used to create location-based or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based <xref:System.Net.Cache.RequestCachePolicy> objects.</span></span>|  
  
 <span data-ttu-id="f494a-118">您可以定義應用程式所提出之所有要求或個別要求的快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-118">You can define a cache policy for all requests made by your application or for individual requests.</span></span> <span data-ttu-id="f494a-119">當您同時指定應用程式層級快取原則和要求層級快取原則時，會使用要求層級原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-119">When you specify both an application-level cache policy and a request-level cache policy, the request-level policy is used.</span></span> <span data-ttu-id="f494a-120">您可以透過程式設計方式或是使用應用程式或電腦組態檔，來指定應用程式層級快取原則。</span><span class="sxs-lookup"><span data-stu-id="f494a-120">You can specify an application-level cache policy programmatically or by using the application or machine configuration files.</span></span> <span data-ttu-id="f494a-121">如需詳細資訊，請參閱 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="f494a-121">For more information, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
 <span data-ttu-id="f494a-122">若要建立快取原則，您必須建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 類別的執行個體來建立原則物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-122">To create a cache policy, you must create a policy object by creating an instance of the <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class.</span></span> <span data-ttu-id="f494a-123">若要在要求上指定原則，請將要求的 <xref:System.Net.WebRequest.CachePolicy%2A> 屬性設定為原則物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-123">To specify the policy on a request, set the request's <xref:System.Net.WebRequest.CachePolicy%2A> property to the policy object.</span></span> <span data-ttu-id="f494a-124">以程式設計方式設定應用程式層級原則時，請將 <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> 屬性設定為原則物件。</span><span class="sxs-lookup"><span data-stu-id="f494a-124">When setting an application-level policy programmatically, set the <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> property to the policy object.</span></span>  
  
 <span data-ttu-id="f494a-125">如需示範如何建立和使用快取原則的程式碼範例，請參閱[設定網路應用程式的快取功能](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="f494a-125">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f494a-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="f494a-126">See Also</span></span>  
 [<span data-ttu-id="f494a-127">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="f494a-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="f494a-128">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="f494a-128">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="f494a-129">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="f494a-129">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="f494a-130">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="f494a-130">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)
