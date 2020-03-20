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
# <a name="how-to-customize-a-time-based-cache-policy"></a>如何：自訂以時間為基礎的快取原則

在建立以時間為基礎的快取原則時，您可以藉由指定最長使用期限、最短有效期限、最長過時或快取同步處理日期的值來自訂快取行為。 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件所提供的建構函式可讓您指定這些值的有效組合。

## <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>建立使用快取同步處理日期之以時間為基礎的快取原則

創建基於時間的緩存策略，該策略通過將<xref:System.DateTime>物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式來使用緩存同步日期：

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

輸出大致如下：

```output
When: 1/14/2004 8:07:30 AM
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>建立依據最短有效期限之以時間為基礎的快取原則

<xref:System.Net.Cache.HttpCacheAgeControl.MinFresh>通過指定`cacheAgeControl`參數值並將<xref:System.TimeSpan>物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式，創建基於最小新鮮度基於時間的緩存策略：

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

對於下列引動過程：

```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));
```

輸出如下：

```output
Level:Default MinFresh:3600
```

## <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則

創建基於最短新鮮度和最大年齡的基於時間的緩存策略，<xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh>指定參數`cacheAgeControl`值並將兩<xref:System.TimeSpan>個物件傳遞給<xref:System.Net.Cache.HttpRequestCachePolicy>建構函式，一個指定資源的最大年齡，第二個指定從緩存返回的物件允許的最低新鮮度：

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

對於下列引動過程：
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

輸出如下：
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>另請參閱

- [網路應用程式的快取管理](cache-management-for-network-applications.md)
- [緩存策略](cache-policy.md)
- [以位置為基礎的快取原則](location-based-cache-policies.md)
- [Time-Based Cache Policies](time-based-cache-policies.md)
- [\<請求緩存>元素（網路設置）](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
