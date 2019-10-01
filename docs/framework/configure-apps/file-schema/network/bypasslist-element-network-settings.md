---
title: <bypasslist> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 1dda43be8c0e0c94bdf7b57b67aa4d403b547f97
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699548"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="73334-102">@no__t 0bypasslist > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="73334-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="73334-103">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="73334-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
[<span data-ttu-id="73334-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="73334-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="73334-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="73334-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="73334-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="73334-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="73334-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<bypasslist >**</span><span class="sxs-lookup"><span data-stu-id="73334-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73334-108">語法</span><span class="sxs-lookup"><span data-stu-id="73334-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73334-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73334-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73334-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73334-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73334-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73334-111">Attributes</span></span>  
 <span data-ttu-id="73334-112">無。</span><span class="sxs-lookup"><span data-stu-id="73334-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="73334-113">子元素</span><span class="sxs-lookup"><span data-stu-id="73334-113">Child Elements</span></span>  
  
|<span data-ttu-id="73334-114">**目**</span><span class="sxs-lookup"><span data-stu-id="73334-114">**Element**</span></span>|<span data-ttu-id="73334-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="73334-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="73334-116">add</span><span class="sxs-lookup"><span data-stu-id="73334-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="73334-117">將 IP 位址或 DNS 名稱新增至 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="73334-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="73334-118">clear</span><span class="sxs-lookup"><span data-stu-id="73334-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="73334-119">清除略過清單。</span><span class="sxs-lookup"><span data-stu-id="73334-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="73334-120">remove</span><span class="sxs-lookup"><span data-stu-id="73334-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="73334-121">從 proxy 略過清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="73334-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73334-122">父項目</span><span class="sxs-lookup"><span data-stu-id="73334-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73334-123">**目**</span><span class="sxs-lookup"><span data-stu-id="73334-123">**Element**</span></span>|<span data-ttu-id="73334-124">**描述**</span><span class="sxs-lookup"><span data-stu-id="73334-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="73334-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="73334-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="73334-126">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="73334-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73334-127">備註</span><span class="sxs-lookup"><span data-stu-id="73334-127">Remarks</span></span>  
 <span data-ttu-id="73334-128">「略過清單」包含正則運算式，其描述的 Uri 是 @no__t 0 實例直接存取，而不是透過 proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="73334-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="73334-129">為此元素指定正則運算式時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="73334-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="73334-130">正則運算式 "[a-z] + \\.contoso\\.com" 會符合 contoso.com 網域中的任何主機，但它也會符合 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="73334-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="73334-131">若只要比對 contoso.com 網域中的主機，請使用錨點（"$"）： "[a-z] + \\.contoso\\.com $"。</span><span class="sxs-lookup"><span data-stu-id="73334-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="73334-132">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="73334-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="73334-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="73334-133">Configuration Files</span></span>  
 <span data-ttu-id="73334-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="73334-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73334-135">範例</span><span class="sxs-lookup"><span data-stu-id="73334-135">Example</span></span>  
 <span data-ttu-id="73334-136">下列範例會將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="73334-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="73334-137">第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="73334-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73334-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73334-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="73334-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="73334-139">Network Settings Schema</span></span>](index.md)
