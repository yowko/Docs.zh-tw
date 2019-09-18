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
# <a name="how-to-customize-a-time-based-cache-policy"></a>HOW TO：自訂以時間為基礎的快取原則
在建立以時間為基礎的快取原則時，您可以藉由指定最長使用期限、最短有效期限、最長過時或快取同步處理日期的值來自訂快取行為。 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件所提供的建構函式可讓您指定這些值的有效組合。  
  
### <a name="to-create-a-time-based-cache-policy-that-uses-a-cache-synchronization-date"></a>建立使用快取同步處理日期之以時間為基礎的快取原則  
  
- 藉由將 <xref:System.DateTime> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立使用快取同步處理日期之以時間為基礎的快取原則。  
  
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
  
 其輸出如下所示：  
  
```output
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness"></a>建立依據最短有效期限之以時間為基礎的快取原則  
  
- 藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MinFresh> 指定為 `cacheAgeControl` 參數值並將 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式，建立依據最短有效期限之以時間為基礎的快取原則。  
  
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
  
 對於下列引動過程：  
  
```csharp
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  

 輸出為：
  
```output
Level:Default MinFresh:3600  
```  
  
### <a name="to-create-a-time-based-cache-policy-that-is-based-on-minimum-freshness-and-maximum-age"></a>建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則  
  
- 藉由將 <xref:System.Net.Cache.HttpCacheAgeControl.MaxAgeAndMinFresh> 指定為 `cacheAgeControl` 參數值並將兩個 <xref:System.TimeSpan> 物件傳遞給 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式 ( 一個用來指定資源的最長使用期限，另一個用來指定從快取傳回的物件所允許的最短有效期限)，建立依據最短有效期限和最長使用期限之以時間為基礎的快取原則。  
  
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
  
 對於下列引動過程：  
  
```csharp
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  

輸出為：
  
```output
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## <a name="see-also"></a>另請參閱

- [網路應用程式的快取管理](cache-management-for-network-applications.md)
- [快取原則](cache-policy.md)
- [以位置為基礎的快取原則](location-based-cache-policies.md)
- [以時間為基礎的快取原則](time-based-cache-policies.md)
- [\<requestCaching> 項目 (網路設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
