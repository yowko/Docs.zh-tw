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
ms.openlocfilehash: 652b8738a201aaa98fa2c5c435fee1a6da91673b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155073"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="50fe4-102">\<添加>元素以進行繞過清單（網路設置）</span><span class="sxs-lookup"><span data-stu-id="50fe4-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="50fe4-103">將 IP 位址或 DNS 名稱添加到代理繞過清單中。</span><span class="sxs-lookup"><span data-stu-id="50fe4-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[<span data-ttu-id="50fe4-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="50fe4-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="50fe4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="50fe4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="50fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="50fe4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="50fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<繞過清單>**](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="50fe4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="50fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<添加>**</span><span class="sxs-lookup"><span data-stu-id="50fe4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50fe4-109">語法</span><span class="sxs-lookup"><span data-stu-id="50fe4-109">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50fe4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="50fe4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="50fe4-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="50fe4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50fe4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="50fe4-112">Attributes</span></span>  
  
|<span data-ttu-id="50fe4-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="50fe4-113">**Attribute**</span></span>|<span data-ttu-id="50fe4-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="50fe4-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="50fe4-115">**位址**</span><span class="sxs-lookup"><span data-stu-id="50fe4-115">**address**</span></span>|<span data-ttu-id="50fe4-116">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="50fe4-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50fe4-117">子元素</span><span class="sxs-lookup"><span data-stu-id="50fe4-117">Child Elements</span></span>  
 <span data-ttu-id="50fe4-118">無。</span><span class="sxs-lookup"><span data-stu-id="50fe4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50fe4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="50fe4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="50fe4-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="50fe4-120">**Element**</span></span>|<span data-ttu-id="50fe4-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="50fe4-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="50fe4-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="50fe4-122">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="50fe4-123">提供一組常規運算式，用於描述不使用代理的位址。</span><span class="sxs-lookup"><span data-stu-id="50fe4-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50fe4-124">備註</span><span class="sxs-lookup"><span data-stu-id="50fe4-124">Remarks</span></span>  
 <span data-ttu-id="50fe4-125">該`add`元素將描述 IP 位址或 DNS 伺服器名稱的正則運算式插入繞過代理伺服器的地址清單中。</span><span class="sxs-lookup"><span data-stu-id="50fe4-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="50fe4-126">`address`屬性的值應是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="50fe4-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="50fe4-127">為此元素指定正則運算式時應小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="50fe4-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="50fe4-128">正則運算式"[a-z].contoso\\\\.com"與contoso.com域中的任何主機匹配，但它也與contoso.com.cpandl.com域中的任何主機匹配。</span><span class="sxs-lookup"><span data-stu-id="50fe4-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="50fe4-129">要僅匹配contoso.com域中的主機，請使用錨點（"$"）："[a-z].contoso.com$"。\\ \\</span><span class="sxs-lookup"><span data-stu-id="50fe4-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="50fe4-130">有關正則運算式的詳細資訊，請參閱。[.NET 框架正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="50fe4-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="50fe4-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="50fe4-131">Configuration Files</span></span>  
 <span data-ttu-id="50fe4-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="50fe4-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fe4-133">範例</span><span class="sxs-lookup"><span data-stu-id="50fe4-133">Example</span></span>  
 <span data-ttu-id="50fe4-134">下面的示例將兩個位址添加到旁路清單中。</span><span class="sxs-lookup"><span data-stu-id="50fe4-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="50fe4-135">第一個繞過contoso.com域中所有伺服器的代理;第二個伺服器繞過其 IP 位址以 192.168 開頭的所有伺服器的代理。</span><span class="sxs-lookup"><span data-stu-id="50fe4-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50fe4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50fe4-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="50fe4-137">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="50fe4-137">Network Settings Schema</span></span>](index.md)
