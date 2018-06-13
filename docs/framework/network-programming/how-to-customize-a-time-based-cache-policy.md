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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fd2856ffcf6b21ba34771c231f608ad725b21763
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390961"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="e85b6-102">如何：自訂以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="e85b6-103">在建立以時間為基礎的快取原則時，您可以藉由指定最長使用期限、最短有效期限、最長過時或快取同步處理日期的值來自訂快取行為。</span><span class="sxs-lookup"><span data-stu-id="e85b6-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="e85b6-104"><xref:System.Net.Cache.HttpRequestCachePolicy> 物件所提供的建構函式可讓您指定這些值的有效組合。</span><span class="sxs-lookup"><span data-stu-id="e85b6-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="e85b6-105">建立使用快取同步處理日期之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
-   <span data-ttu-id="e85b6-106">藉由將 <xref:System.DateTime> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立使用快取同步處理日期之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="e85b6-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateLastSyncPolicy(DateTime when)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(when);  
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
  
 <span data-ttu-id="e85b6-107">其輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="e85b6-107">The output is similar to the following:</span></span>  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="e85b6-108">建立依據最短有效期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
-   <span data-ttu-id="e85b6-109">藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> 指定為 `cacheAgeControl` 參數值並將 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立依據最短有效期限之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="e85b6-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateMinFreshPolicy(TimeSpan span)  
    {  
        HttpRequestCachePolicy policy =   
            new HttpRequestCachePolicy(HttpCacheAgeControl.MinFresh, span);  
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
  
 <span data-ttu-id="e85b6-110">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="e85b6-110">For the following invocation:</span></span>  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="e85b6-111">建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-111">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
-   <span data-ttu-id="e85b6-112">藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> 指定為 `cacheAgeControl` 參數值並將兩個 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式 ( 一個用來指定資源的最長使用期限，另一個用來指定從快取傳回的物件所允許的最短有效期限)，建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="e85b6-112">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
    ```csharp  
    public static HttpRequestCachePolicy CreateFreshAndAgePolicy(TimeSpan freshMinimum, TimeSpan ageMaximum)  
    {  
        HttpRequestCachePolicy policy =   
        new HttpRequestCachePolicy(HttpCacheAgeControl.MaxAgeAndMinFresh, ageMaximum, freshMinimum);  
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
  
 <span data-ttu-id="e85b6-113">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="e85b6-113">For the following invocation:</span></span>  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="e85b6-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e85b6-114">See Also</span></span>  
 [<span data-ttu-id="e85b6-115">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="e85b6-115">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="e85b6-116">快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-116">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="e85b6-117">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-117">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="e85b6-118">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="e85b6-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="e85b6-119">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="e85b6-119">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
