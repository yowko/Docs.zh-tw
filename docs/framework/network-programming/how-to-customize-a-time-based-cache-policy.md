---
title: 如何：自訂以時間為基礎的快取原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: 1a2ba404e333eeec2a23758c834876d0df5aba81
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040638"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="1a45b-102">如何：自訂以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1a45b-102">How to: customize a time-based cache policy</span></span>

<span data-ttu-id="1a45b-103">在建立以時間為基礎的快取原則時，您可以藉由指定最長使用期限、最短有效期限、最長過時或快取同步處理日期的值來自訂快取行為。</span><span class="sxs-lookup"><span data-stu-id="1a45b-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="1a45b-104"><xref:System.Net.Cache.HttpRequestCachePolicy> 物件所提供的建構函式可讓您指定這些值的有效組合。</span><span class="sxs-lookup"><span data-stu-id="1a45b-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="1a45b-105">建立使用快取同步處理日期之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1a45b-105">To create a time-based cache policy that uses a cache synchronization date</span></span>

<span data-ttu-id="1a45b-106">創建基於時間的緩存策略，該策略通過將<xref:System.DateTime>物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式來使用緩存同步日期：</span><span class="sxs-lookup"><span data-stu-id="1a45b-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)
{
    var policy = new HttpRequestCachePolicy(when);
    Console.WriteLine("When: {0}", when);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateLastSyncPolicy([when] As DateTime) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy([when])
    Console.WriteLine("When: {0}", [when])
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="1a45b-107">輸出大致如下：</span><span class="sxs-lookup"><span data-stu-id="1a45b-107">The output is similar to the following:</span></span>

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="1a45b-108">建立依據最短有效期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1a45b-108">To create a time-based cache policy that is based on minimum freshness</span></span>

<span data-ttu-id="1a45b-109"><xref:System.Net.Cache.HttpCacheAgeControl.MinFresh>通過指定`cacheAgeControl`參數值並將<xref:System.TimeSpan>物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式，創建基於最小新鮮度基於時間的緩存策略：</span><span class="sxs-lookup"><span data-stu-id="1a45b-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor:</span></span>

```csharp
public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateMinFreshPolicy(span As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="1a45b-110">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="1a45b-110">For the following invocation:</span></span>

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

<span data-ttu-id="1a45b-111">輸出如下：</span><span class="sxs-lookup"><span data-stu-id="1a45b-111">The output is:</span></span>

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="1a45b-112">建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1a45b-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>

<span data-ttu-id="1a45b-113">創建基於最短新鮮度和最大年齡的基於時間的緩存策略，<xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh>指定參數`cacheAgeControl`值並將兩<xref:System.TimeSpan>個物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式，一個指定資源的最大年齡，第二個指定從緩存返回的物件允許的最低新鮮度：</span><span class="sxs-lookup"><span data-stu-id="1a45b-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache:</span></span>

```csharp
public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)
{
    var policy = new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);
    Console.WriteLine(policy.ToString());
    return policy;
}
```

```vb
Public Shared Function CreateFreshAndAgePolicy(freshMinimum As TimeSpan, ageMaximum As TimeSpan) As HttpRequestCachePolicy
    Dim policy As New HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum)
    Console.WriteLine(policy.ToString())
    Return policy
End Function
```

<span data-ttu-id="1a45b-114">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="1a45b-114">For the following invocation:</span></span>
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="1a45b-115">輸出如下：</span><span class="sxs-lookup"><span data-stu-id="1a45b-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a45b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a45b-116">See also</span></span>

- [<span data-ttu-id="1a45b-117">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="1a45b-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="1a45b-118">緩存策略</span><span class="sxs-lookup"><span data-stu-id="1a45b-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="1a45b-119">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="1a45b-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="1a45b-120">Time-Based Cache Policies</span><span class="sxs-lookup"><span data-stu-id="1a45b-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="1a45b-121">\<請求緩存>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="1a45b-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
