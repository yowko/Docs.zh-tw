---
title: "如何：為應用程式設定以時間為基礎的預設快取原則 | Microsoft Docs"
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
  - "快取 [.NET Framework]，以時間為基礎的原則"
  - "以時間為基礎的預設快取原則"
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# 如何：為應用程式設定以時間為基礎的預設快取原則
預設時間為主的快取原則可讓應用程式有標題定義它的快取行為所傳送之快取資源和中定義的快取行為 Section 13 和第 14 節 RFC 2616， [http:\/\/www.ietf.org](http://www.ietf.org/)網址為。  這是大部分應用程式的快取行為。  
  
### 設定應用程式的預設自動原則  
  
1.  建立預設時間為主的原則物件。  
  
2.  設定原則物件做為應用程式定義域的預設值。  
  
## 範例  
 本節中的兩個範例都會產生相同的原則。  
  
 下列範例會建立預設時間架構原則並將其設定為應用程式定義域的預設值。  
  
```csharp  
public static void SetDefaultTimeBasedPolicy ()  
{  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy ()  
    Dim policy = New HttpRequestCachePolicy ()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
```  
  
 如下列範例所示，您也可以建立預設時間為主的快取原則使用 <xref:System.Net.Cache.RequestCachePolicy> 類別:  
  
```csharp  
public static void SetDefaultTimeBasedPolicy2()  
{  
    RequestCachePolicy policy = new RequestCachePolicy ();  
    HttpWebRequest.DefaultCachePolicy = policy ;  
}  
```  
  
```vb  
Public Shared Sub SetDefaultTimeBasedPolicy2()  
    Dim policy As New RequestCachePolicy()  
    HttpWebRequest.DefaultCachePolicy = policy  
End Sub  
  
```  
  
## 請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)   
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)   
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)   
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)   
 [\<requestCaching\> 項目 \(網路設定\)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)