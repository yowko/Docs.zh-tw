---
title: "如何：自訂以時間為基礎的快取原則 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "以時間為基礎的快取原則"
  - "自訂以時間為基礎的快取原則"
  - "快取 [.NET Framework]，以時間為基礎的原則"
ms.assetid: 8d84f936-2376-4356-9264-03162e0f9279
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 如何：自訂以時間為基礎的快取原則
當建立以時間為主的快取原則時，您可以指定屬性的值可以自訂快取行為在最長保留期限、最短有效期限、最大為組態或快取同步處理日期。  <xref:System.Net.Cache.HttpRequestCachePolicy> 物件提供可讓您指定這些值的有效組合的多個建構函式。  
  
### 建立一個使用快取同步處理日期的以時間為主的快取原則  
  
-   建立傳遞至 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式的 <xref:System.DateTime> 物件使用一個快取同步處理日期的以時間為主的快取原則。  
  
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
  
 類似如下的輸出:  
  
```  
When: 1/14/2004 8:07:30 AM  
Level:Default CacheSyncDate:1/14/2004 8:07:30 AM  
```  
  
### 若要根據最短有效期限以時間為主的快取原則  
  
-   若要根據最短有效期限藉由指定 <xref:System.Net.Cache.HttpCacheAgeControl> 做為 `cacheAgeControl` 參數值和傳遞至 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式的 <xref:System.TimeSpan> 物件的以時間為主的快取原則。  
  
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
  
 下列引動過程的:  
  
```  
CreateMinFreshPolicy(new TimeSpan(1,0,0));  
```  
  
```  
Level:Default MinFresh:3600  
  
```  
  
### 若要根據最短有效期限和最長保留期限的以時間為主的快取原則  
  
-   若要根據最短有效期限和最長保留期限藉由指定 <xref:System.Net.Cache.HttpCacheAgeControl> 做為 `cacheAgeControl` 參數值和傳遞至 <xref:System.Net.Cache.HttpRequestCachePolicy> 建構函式有兩種 <xref:System.TimeSpan> 物件的以時間為主的快取原則，指定最長保留期限的一個資源和一秒為從快取傳回之物件所允許的最短有效期限。  
  
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
  
 下列引動過程的:  
  
```  
CreateFreshAndAgePolicy(new TimeSpan(5,0,0), new TimeSpan(10,0,0));  
```  
  
```  
Level:Default MaxAge:36000 MinFresh:18000  
```  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)