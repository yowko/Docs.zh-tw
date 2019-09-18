---
title: 作法：自訂以時間為基礎的快取原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- customizing time-based cache policies
- cache [.NET Framework], time-based policies
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
ms.openlocfilehash: c28c6daf9b873a19291b1636112eae6546412be2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048321"
---
# <a name="how-to-customize-a-time-based-cache-policy"></a><span data-ttu-id="9c255-102">HOW TO：自訂以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-102">How to: Customize a Time-Based Cache Policy</span></span>
<span data-ttu-id="9c255-103">在建立以時間為基礎的快取原則時，您可以藉由指定最長使用期限、最短有效期限、最長過時或快取同步處理日期的值來自訂快取行為。</span><span class="sxs-lookup"><span data-stu-id="9c255-103">When creating a time-based cache policy, you can customize caching behavior by specifying values for maximum age, minimum freshness, maximum staleness, or cache synchronization date.</span></span> <span data-ttu-id="9c255-104"><xref:System.Net.Cache.HttpRequestCachePolicy> 物件所提供的建構函式可讓您指定這些值的有效組合。</span><span class="sxs-lookup"><span data-stu-id="9c255-104">The <xref:System.Net.Cache.HttpRequestCachePolicy> object provides several constructors that allow you to specify valid combinations of these values.</span></span>  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a><span data-ttu-id="9c255-105">建立使用快取同步處理日期之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-105">To create a time-based cache policy that uses a cache synchronization date</span></span>  
  
- <span data-ttu-id="9c255-106">藉由將 <xref:System.DateTime> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立使用快取同步處理日期之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="9c255-106">Create a time-based cache policy that uses a cache synchronization date by passing a <xref:System.DateTime> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="9c255-107">其輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="9c255-107">The output is similar to the following:</span></span>  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a><span data-ttu-id="9c255-108">建立依據最短有效期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-108">To create a time-based cache policy that is based on minimum freshness</span></span>  
  
- <span data-ttu-id="9c255-109">藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> 指定為 `cacheAgeControl` 參數值並將 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立依據最短有效期限之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="9c255-109">Create a time-based cache policy that is based on minimum freshness by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> as the `cacheAgeControl` parameter value and passing a <xref:System.TimeSpan> object to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor.</span></span>  
  
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
  
 <span data-ttu-id="9c255-110">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="9c255-110">For the following invocation:</span></span>  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 <span data-ttu-id="9c255-111">輸出為：</span><span class="sxs-lookup"><span data-stu-id="9c255-111">The output is:</span></span>
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a><span data-ttu-id="9c255-112">建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-112">To create a time-based cache policy that is based on minimum freshness and maximum age</span></span>  
  
- <span data-ttu-id="9c255-113">藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> 指定為 `cacheAgeControl` 參數值並將兩個 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式 ( 一個用來指定資源的最長使用期限，另一個用來指定從快取傳回的物件所允許的最短有效期限)，建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則。</span><span class="sxs-lookup"><span data-stu-id="9c255-113">Create a time-based cache policy that is based on minimum freshness and maximum age by specifying <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> as the `cacheAgeControl` parameter value and passing two <xref:System.TimeSpan> objects to the <xref:System.Net.Cache.HttpRequestCachePolicy> constructor, one to specify the maximum age for resources and a second to specify the minimum freshness permitted for an object returned from the cache.</span></span>  
  
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
  
 <span data-ttu-id="9c255-114">對於下列引動過程：</span><span class="sxs-lookup"><span data-stu-id="9c255-114">For the following invocation:</span></span>  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

<span data-ttu-id="9c255-115">輸出為：</span><span class="sxs-lookup"><span data-stu-id="9c255-115">The output is:</span></span>
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c255-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c255-116">See also</span></span>

- [<span data-ttu-id="9c255-117">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="9c255-117">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="9c255-118">快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-118">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="9c255-119">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-119">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="9c255-120">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="9c255-120">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="9c255-121">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="9c255-121">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
