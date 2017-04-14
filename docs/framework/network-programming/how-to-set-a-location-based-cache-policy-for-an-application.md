---
title: "如何：為應用程式設定以位置為基礎的快取原則 | Microsoft Docs"
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
  - "明確定義快取行為"
  - "以位置為基礎的快取原則"
  - "本機快取"
  - "要求快取原則"
  - "快取 [.NET Framework]，以位置為基礎的原則"
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# 如何：為應用程式設定以位置為基礎的快取原則
以位置的快取原則允許應用程式明確地定義根據要求的資源位置的快取行為。  本主題會示範如何設定快取原則的方式。  如需設定應用程式的原則的資訊使用組態檔，請參閱 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)。  
  
### 設定應用程式的以位置為主的快取原則  
  
1.  建立 <xref:System.Net.Cache.RequestCachePolicy> 或 <xref:System.Net.Cache.HttpRequestCachePolicy> 物件。  
  
2.  設定原則物件做為應用程式定義域的預設值。  
  
### 若要設定要採取的原則要求會從快取中的資源  
  
-   如果已建立、、和則會從快取的要求資源的原則，將要求傳送至伺服器，您可以設定快取層級。 <xref:System.Net.Cache.HttpRequestCacheLevel>。  要求可以由用戶端和伺服器之間的所有快取滿足，包含遠端用戶端快取。  
  
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
  
### 設定讓所有快取提供資源的原則  
  
-   建立讓所有快取提供所要求的資源是透過設定快取層級。 <xref:System.Net.Cache.HttpRequestCacheLevel>的原則。  這個原則層級從本機快取區移除資源，如果它出現並指示遠端快取它們也應該移除資源。  
  
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
  
### 若要設定傳回的原則要求資源時，才會在本機快取。  
  
-   建立會傳回所要求資源的原則，才會在本機快取可以設定快取層級。 <xref:System.Net.Cache.HttpRequestCacheLevel>。  如果要求的資源不在快取中， <xref:System.Net.WebException> 擲回例外狀況。  
  
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
  
### 設定可防止本機快取提供資源的原則  
  
-   建立讓本機快取提供所要求的資源是透過設定快取層級。 <xref:System.Net.Cache.HttpRequestCacheLevel>的原則。  如果要求的資源已中繼快取並成功重新確認，中繼快取可以提供需要的資源。  
  
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
  
### 設定讓所有快取提供所要求資源的原則  
  
-   建立讓所有快取提供所要求的資源是透過設定快取層級。 <xref:System.Net.Cache.HttpRequestCacheLevel>的原則。  伺服器傳回的資源可以儲存在快取中。  
  
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
  
### 若要設定讓所有快取提供的原則要求資源時，如果伺服器上的資源比這個快取複本不新  
  
-   建立讓所有快取可以設定快取層級提供所要求資源的原則，如果伺服器上的資源比這個快取複本不提供新 <xref:System.Net.Cache.HttpRequestCacheLevel>。  
  
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
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)