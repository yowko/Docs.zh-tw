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
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="741cb-102">作法：為應用程式設定以時間為基礎的預設快取原則</span><span class="sxs-lookup"><span data-stu-id="741cb-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="741cb-103">以時間為基礎的預設快取原則，可讓應用程式擁有與快取資源一起傳送之標頭所定義的快取行為，以及 RFC 2616 的第 13 節與第 14 節中定義的快取行為 (可從[網際網路工程任務推動小組 (IETF)](https://www.ietf.org/) 網站取得)。</span><span class="sxs-lookup"><span data-stu-id="741cb-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span> <span data-ttu-id="741cb-104">這是適用於大部分應用程式的快取行為。</span><span class="sxs-lookup"><span data-stu-id="741cb-104">This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="741cb-105">設定應用程式的預設自動原則</span><span class="sxs-lookup"><span data-stu-id="741cb-105">To set the default automatic policy for an application</span></span>  
  
1. <span data-ttu-id="741cb-106">建立以時間為基礎的預設原則物件。</span><span class="sxs-lookup"><span data-stu-id="741cb-106">Create a default time-based policy object.</span></span>  
  
2. <span data-ttu-id="741cb-107">設定原則物件作為應用程式定義域的預設值。</span><span class="sxs-lookup"><span data-stu-id="741cb-107">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="741cb-108">範例</span><span class="sxs-lookup"><span data-stu-id="741cb-108">Example</span></span>  
 <span data-ttu-id="741cb-109">本節中的兩個範例會產生相同的原則。</span><span class="sxs-lookup"><span data-stu-id="741cb-109">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="741cb-110">下列範例會建立以時間為基礎的預設原則，並將它設定為應用程式定義域的預設值。</span><span class="sxs-lookup"><span data-stu-id="741cb-110">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="741cb-111">您也可以使用 <xref:System.Net.Cache.RequestCachePolicy> 類別來建立以時間為基礎的預設快取原則，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="741cb-111">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="741cb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="741cb-112">See also</span></span>

- [<span data-ttu-id="741cb-113">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="741cb-113">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="741cb-114">快取原則</span><span class="sxs-lookup"><span data-stu-id="741cb-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="741cb-115">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="741cb-115">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="741cb-116">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="741cb-116">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="741cb-117">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="741cb-117">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
