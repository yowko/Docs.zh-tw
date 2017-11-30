---
title: "如何：為應用程式設定以時間為基礎的預設快取原則"
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
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ae864b5f22f469d9a60b9faba90a5a66c65e8172
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>如何：為應用程式設定以時間為基礎的預設快取原則
以時間為基礎的預設快取原則，可讓應用程式擁有與快取資源一起傳送之標頭所定義的快取行為，以及 RFC 2616 的第 13 節與第 14 節中定義的快取行為 (可從 [http://www.ietf.org](http://www.ietf.org/) 取得)。這是適用於大部分應用程式的快取行為。  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>設定應用程式的預設自動原則  
  
1.  建立以時間為基礎的預設原則物件。  
  
2.  設定原則物件作為應用程式定義域的預設值。  
  
## <a name="example"></a>範例  
 本節中的兩個範例會產生相同的原則。  
  
 下列範例會建立以時間為基礎的預設原則，並將它設定為應用程式定義域的預設值。  
  
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
  
 您也可以使用 <xref:System.Net.Cache.RequestCachePolicy> 類別來建立以時間為基礎的預設快取原則，如下列範例所示：  
  
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
  
## <a name="see-also"></a>另請參閱  
 [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [快取原則](../../../docs/framework/network-programming/cache-policy.md)  
 [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
