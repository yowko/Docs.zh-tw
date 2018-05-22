---
title: 如何：為應用程式設定以時間為基礎的預設快取原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time-based cache policies
- cache [.NET Framework], time-based policies
- default time-based cache policy
ms.assetid: 6bfce066-a2e7-4add-a05e-85c12ec9f07f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 021a13b9124cf54712643e33cbf0ca77ec828b27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-default-time-based-cache-policy-for-an-application"></a><span data-ttu-id="534ff-102">如何：為應用程式設定以時間為基礎的預設快取原則</span><span class="sxs-lookup"><span data-stu-id="534ff-102">How to: Set the Default Time-Based Cache Policy for an Application</span></span>
<span data-ttu-id="534ff-103">以時間為基礎的預設快取原則，可讓應用程式擁有與快取資源一起傳送之標頭所定義的快取行為，以及 RFC 2616 的第 13 節與第 14 節中定義的快取行為 (可從 [http://www.ietf.org](http://www.ietf.org/) 取得)。這是適用於大部分應用程式的快取行為。</span><span class="sxs-lookup"><span data-stu-id="534ff-103">The default time-based cache policy allows an application to have its cache behavior defined by the headers sent with the cached resource and the cache behavior defined in sections 13 and 14 of RFC 2616, available at [http://www.ietf.org](http://www.ietf.org/). This is the appropriate cache behavior for most applications.</span></span>  
  
### <a name="to-set-the-default-automatic-policy-for-an-application"></a><span data-ttu-id="534ff-104">設定應用程式的預設自動原則</span><span class="sxs-lookup"><span data-stu-id="534ff-104">To set the default automatic policy for an application</span></span>  
  
1.  <span data-ttu-id="534ff-105">建立以時間為基礎的預設原則物件。</span><span class="sxs-lookup"><span data-stu-id="534ff-105">Create a default time-based policy object.</span></span>  
  
2.  <span data-ttu-id="534ff-106">設定原則物件作為應用程式定義域的預設值。</span><span class="sxs-lookup"><span data-stu-id="534ff-106">Set the policy object as the default for the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="534ff-107">範例</span><span class="sxs-lookup"><span data-stu-id="534ff-107">Example</span></span>  
 <span data-ttu-id="534ff-108">本節中的兩個範例會產生相同的原則。</span><span class="sxs-lookup"><span data-stu-id="534ff-108">The two examples in this section produce identical policies.</span></span>  
  
 <span data-ttu-id="534ff-109">下列範例會建立以時間為基礎的預設原則，並將它設定為應用程式定義域的預設值。</span><span class="sxs-lookup"><span data-stu-id="534ff-109">The following example creates a default time-based policy and sets it as the default for the application domain.</span></span>  
  
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
  
 <span data-ttu-id="534ff-110">您也可以使用 <xref:System.Net.Cache.RequestCachePolicy> 類別來建立以時間為基礎的預設快取原則，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="534ff-110">You can also create the default time-based cache policy using the <xref:System.Net.Cache.RequestCachePolicy> class as shown in the following example:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="534ff-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="534ff-111">See Also</span></span>  
 [<span data-ttu-id="534ff-112">網路應用程式的快取管理</span><span class="sxs-lookup"><span data-stu-id="534ff-112">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 [<span data-ttu-id="534ff-113">快取原則</span><span class="sxs-lookup"><span data-stu-id="534ff-113">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 [<span data-ttu-id="534ff-114">以位置為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="534ff-114">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 [<span data-ttu-id="534ff-115">以時間為基礎的快取原則</span><span class="sxs-lookup"><span data-stu-id="534ff-115">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 [<span data-ttu-id="534ff-116">\<requestCaching> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="534ff-116">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)
