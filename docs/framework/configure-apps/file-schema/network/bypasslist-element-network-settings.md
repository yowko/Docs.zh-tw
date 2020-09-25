---
title: <bypasslist> 項目 (網路設定)
description: <bypasslist>Network settings 元素提供一組正則運算式，用來描述未在 .NET Framework 中使用 proxy 的位址。
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: 58cdcf046b2a5a292493c5704739b22aa4ec4f17
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178407"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="a1016-103">\<bypasslist> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="a1016-103">\<bypasslist> Element (Network Settings)</span></span>

<span data-ttu-id="a1016-104">提供一組正則運算式，用來描述未使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="a1016-104">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**

## <a name="syntax"></a><span data-ttu-id="a1016-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1016-105">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1016-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a1016-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a1016-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a1016-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1016-108">屬性</span><span class="sxs-lookup"><span data-stu-id="a1016-108">Attributes</span></span>  

 <span data-ttu-id="a1016-109">無。</span><span class="sxs-lookup"><span data-stu-id="a1016-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a1016-110">子元素</span><span class="sxs-lookup"><span data-stu-id="a1016-110">Child Elements</span></span>  
  
|<span data-ttu-id="a1016-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="a1016-111">**Element**</span></span>|<span data-ttu-id="a1016-112">**說明**</span><span class="sxs-lookup"><span data-stu-id="a1016-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a1016-113">add</span><span class="sxs-lookup"><span data-stu-id="a1016-113">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a1016-114">將 IP 位址或 DNS 名稱新增至 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="a1016-114">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="a1016-115">清除</span><span class="sxs-lookup"><span data-stu-id="a1016-115">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a1016-116">清除 [略過] 清單。</span><span class="sxs-lookup"><span data-stu-id="a1016-116">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="a1016-117">remove</span><span class="sxs-lookup"><span data-stu-id="a1016-117">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="a1016-118">從 proxy 略過清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="a1016-118">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a1016-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a1016-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a1016-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="a1016-120">**Element**</span></span>|<span data-ttu-id="a1016-121">**說明**</span><span class="sxs-lookup"><span data-stu-id="a1016-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a1016-122">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="a1016-122">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="a1016-123">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a1016-123">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1016-124">備註</span><span class="sxs-lookup"><span data-stu-id="a1016-124">Remarks</span></span>  

 <span data-ttu-id="a1016-125">略過清單包含正則運算式，可描述 <xref:System.Net.WebRequest> 實例直接存取而非透過 proxy 伺服器存取的 uri。</span><span class="sxs-lookup"><span data-stu-id="a1016-125">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="a1016-126">為此元素指定正則運算式時，請特別小心。</span><span class="sxs-lookup"><span data-stu-id="a1016-126">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="a1016-127">正則運算式 "[a-z] + \\ . \\ .com" 符合 contoso.com 網域中的任何主機，但它也符合 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="a1016-127">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="a1016-128">若只要比對 contoso.com 網域中的主機，請使用錨點 ( "$" ) ： "[a-z] + \\ . \\ .com $"。</span><span class="sxs-lookup"><span data-stu-id="a1016-128">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="a1016-129">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a1016-129">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a1016-130">組態檔</span><span class="sxs-lookup"><span data-stu-id="a1016-130">Configuration Files</span></span>  

 <span data-ttu-id="a1016-131">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="a1016-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1016-132">範例</span><span class="sxs-lookup"><span data-stu-id="a1016-132">Example</span></span>  

 <span data-ttu-id="a1016-133">下列範例會將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="a1016-133">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="a1016-134">第一個會針對 contoso.com 網域中的所有伺服器略過 proxy;第二個會針對 IP 位址開頭為192.168 的所有伺服器略過 proxy。</span><span class="sxs-lookup"><span data-stu-id="a1016-134">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1016-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1016-135">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a1016-136">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a1016-136">Network Settings Schema</span></span>](index.md)
