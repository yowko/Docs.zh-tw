---
title: "網路應用程式的快取管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 458a1e67e9ca4ff3a36f1b0c69fcc4bdc00be3e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="0d60c-102">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="0d60c-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="0d60c-103">本主題和其相關子主題描述如何使用 <xref:System.Net.WebClient>、<xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.FtpWebRequest> 類別所取得資源的快取。</span><span class="sxs-lookup"><span data-stu-id="0d60c-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="0d60c-104">快取提供應用程式已要求的資源暫時儲存位置。</span><span class="sxs-lookup"><span data-stu-id="0d60c-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="0d60c-105">如果應用程式多次要求相同的資源，則可以從快取傳回資源，避免從伺服器重新要求它的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="0d60c-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="0d60c-106">快取可以透過減少取得所要求資源所需的時間，來改善應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="0d60c-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="0d60c-107">快取也可以減少往返伺服器的次數，來降低網路流量。</span><span class="sxs-lookup"><span data-stu-id="0d60c-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="0d60c-108">雖然快取可改善效能，但是會增加傳回給應用程式的資源過時的風險，這表示它與未使用快取時由伺服器所傳送的資源不同。</span><span class="sxs-lookup"><span data-stu-id="0d60c-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="0d60c-109">快取可讓未經授權的使用者或處理序讀取敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="0d60c-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="0d60c-110">可以從快取擷取所快取的已驗證回應，而不需要額外授權。</span><span class="sxs-lookup"><span data-stu-id="0d60c-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="0d60c-111">如果啟用快取，請將 <xref:System.Net.WebRequest.CachePolicy%2A> 變更為 <xref:System.Net.Cache.RequestCacheLevel.BypassCache> 或 <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore>，以停用此要求的快取。</span><span class="sxs-lookup"><span data-stu-id="0d60c-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="0d60c-112">基於安全性考量，**不**建議針對中介層案例進行快取。</span><span class="sxs-lookup"><span data-stu-id="0d60c-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d60c-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="0d60c-113">In This Section</span></span>  
 [<span data-ttu-id="0d60c-114">快取原則</span><span class="sxs-lookup"><span data-stu-id="0d60c-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="0d60c-115">說明快取原則是什麼，以及如何定義快取原則。</span><span class="sxs-lookup"><span data-stu-id="0d60c-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="0d60c-116">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="0d60c-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="0d60c-117">定義可用於超文字傳輸通訊協定 (http 和 https) 資源的每種以位置為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="0d60c-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="0d60c-118">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="0d60c-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="0d60c-119">描述可用來自訂以時間為基礎的快取原則的條件。</span><span class="sxs-lookup"><span data-stu-id="0d60c-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="0d60c-120">設定網路應用程式的快取功能</span><span class="sxs-lookup"><span data-stu-id="0d60c-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="0d60c-121">描述如何以程式設計方式建立快取原則以及使用快取的要求。</span><span class="sxs-lookup"><span data-stu-id="0d60c-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0d60c-122">參考資料</span><span class="sxs-lookup"><span data-stu-id="0d60c-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="0d60c-123">可定義類型和列舉，這些類型和列舉是用來定義使用 <xref:System.Net.WebRequest>、<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.FtpWebRequest> 類別所取得之資源的快取原則。</span><span class="sxs-lookup"><span data-stu-id="0d60c-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
