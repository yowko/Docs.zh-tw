---
title: "如何：為應用程式設定以位置為基礎的快取原則"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a145bf30930c9be81dc92f3a9f1eebda046b7e8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>如何：為應用程式設定以位置為基礎的快取原則
以位置為基礎的快取原則，可讓應用程式明確地定義根據所要求資源位置的快取行為。 本主題將示範如何以程式設計方式設定快取原則。 如需使用組態檔為應用程式設定原則的詳細資訊，請參閱 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)。  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>為應用程式設定以位置為基礎的快取原則  
  
1.  建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。  
  
2.  設定原則物件作為應用程式定義域的預設值。  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>設定從快取中取得所要求資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable> 來建立下列原則：從快取中取得可用的所要求資源，否則將要求傳送到伺服器。 用戶端與伺服器之間的任何快取都可以滿足要求，包括遠端快取。  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>設定防止任何快取提供資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore> 來建立下列原則：防止任何快取提供所要求的資源。 此原則層級會從本機快取中移除存在的資源，並且向遠端快取指出它們也應該移除資源。  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>設定唯有所要求的資源位於本機快取中時，才會傳回這些資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly> 來建立下列原則：唯有所要求的資源位於本機快取中時，才會傳回這些資源。 如果所要求的資源不在快取中，則會擲回 <xref:System.Net.WebException> 例外狀況。  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>設定防止本機快取提供資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh> 來建立下列原則：防止本機快取提供所要求的資源。 如果所要求的資源位於中繼快取中，而且已成功重新驗證，則中繼快取可以提供所要求的資源。  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>設定防止任何快取提供所要求資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Reload> 來建立下列原則：防止任何快取提供所要求的資源。 伺服器傳回的資源可以儲存在快取中。  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>設定伺服器上的資源並未比快取複本更新時，可讓任何快取提供所要求資源的原則  
  
-   藉由將快取層級設定為 <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate> 來建立下列原則：伺服器上的資源並未比快取複本更新時，可讓任何快取提供所要求的資源。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)  
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
