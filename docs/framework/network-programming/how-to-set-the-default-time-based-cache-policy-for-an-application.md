---
title: 作法：為應用程式設定以時間為基礎的預設快取原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
ms.openlocfilehash: 99f9905109a4deabe3cfb2e3616913e84f565cb7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299120"
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a>作法：為應用程式設定以時間為基礎的預設快取原則
以時間為基礎的預設快取原則，可讓應用程式擁有與快取資源一起傳送之標頭所定義的快取行為，以及 RFC 2616 的第 13 節與第 14 節中定義的快取行為 (可從[網際網路工程任務推動小組 (IETF)](https://www.ietf.org/) 網站取得)。 這是適用於大部分應用程式的快取行為。  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a>設定應用程式的預設自動原則  
  
1. 建立以時間為基礎的預設原則物件。  
  
2. 設定原則物件作為應用程式定義域的預設值。  
  
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

- [網路應用程式的快取管理](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [快取原則](../../../docs/framework/network-programming/cache-policy.md)
- [以位置為基礎的快取原則](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [以時間為基礎的快取原則](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching> 項目 (網路設定)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
