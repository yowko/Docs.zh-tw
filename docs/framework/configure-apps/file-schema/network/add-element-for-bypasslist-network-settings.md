---
title: bypasslist 的 <add> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
ms.openlocfilehash: 1db0ba3b0a213de1175e6e0cee347753d2a413b7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699604"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="a10a1-102">適用于 bypasslist 的 @no__t 0add > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="a10a1-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="a10a1-103">將 IP 位址或 DNS 名稱新增至 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="a10a1-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="a10a1-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a10a1-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a10a1-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a10a1-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="a10a1-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a10a1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="a10a1-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a10a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="a10a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="a10a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10a1-109">語法</span><span class="sxs-lookup"><span data-stu-id="a10a1-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a10a1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a10a1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a10a1-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a10a1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a10a1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a10a1-112">Attributes</span></span>  
  
|<span data-ttu-id="a10a1-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="a10a1-113">**Attribute**</span></span>|<span data-ttu-id="a10a1-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="a10a1-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="a10a1-115">**address**</span><span class="sxs-lookup"><span data-stu-id="a10a1-115">**address**</span></span>|<span data-ttu-id="a10a1-116">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="a10a1-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a10a1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a10a1-117">Child Elements</span></span>  
 <span data-ttu-id="a10a1-118">無。</span><span class="sxs-lookup"><span data-stu-id="a10a1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a10a1-119">父項目</span><span class="sxs-lookup"><span data-stu-id="a10a1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a10a1-120">**目**</span><span class="sxs-lookup"><span data-stu-id="a10a1-120">**Element**</span></span>|<span data-ttu-id="a10a1-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="a10a1-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a10a1-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="a10a1-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="a10a1-123">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="a10a1-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a10a1-124">備註</span><span class="sxs-lookup"><span data-stu-id="a10a1-124">Remarks</span></span>  
 <span data-ttu-id="a10a1-125">@No__t-0 元素會在略過 proxy 伺服器的地址清單中，插入描述 IP 位址或 DNS 伺服器名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="a10a1-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="a10a1-126">@No__t-0 屬性的值應該是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="a10a1-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="a10a1-127">為此元素指定正則運算式時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="a10a1-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="a10a1-128">正則運算式 "[a-z] + \\.contoso\\.com" 會符合 contoso.com 網域中的任何主機，但它也會符合 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="a10a1-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="a10a1-129">若只要比對 contoso.com 網域中的主機，請使用錨點（"$"）： "[a-z] + \\.contoso\\.com $"。</span><span class="sxs-lookup"><span data-stu-id="a10a1-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="a10a1-130">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="a10a1-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a10a1-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="a10a1-131">Configuration Files</span></span>  
 <span data-ttu-id="a10a1-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="a10a1-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a10a1-133">範例</span><span class="sxs-lookup"><span data-stu-id="a10a1-133">Example</span></span>  
 <span data-ttu-id="a10a1-134">下列範例會將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="a10a1-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="a10a1-135">第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="a10a1-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a10a1-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a10a1-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="a10a1-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a10a1-137">Network Settings Schema</span></span>](index.md)
