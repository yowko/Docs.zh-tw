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
ms.openlocfilehash: 97e69a4978aa4700d13a994619a65312cf70aeaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154942"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="dbf49-102">\<繞過清單>元素（網路設置）</span><span class="sxs-lookup"><span data-stu-id="dbf49-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="dbf49-103">提供一組常規運算式，用於描述不使用代理的位址。</span><span class="sxs-lookup"><span data-stu-id="dbf49-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  

<span data-ttu-id="dbf49-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dbf49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dbf49-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="dbf49-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="dbf49-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<預設代理>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="dbf49-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="dbf49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<繞過清單>**</span><span class="sxs-lookup"><span data-stu-id="dbf49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bypasslist>**</span></span>

## <a name="syntax"></a><span data-ttu-id="dbf49-108">語法</span><span class="sxs-lookup"><span data-stu-id="dbf49-108">Syntax</span></span>  
  
```xml  
<bypasslist>
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbf49-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dbf49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dbf49-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dbf49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbf49-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dbf49-111">Attributes</span></span>  
 <span data-ttu-id="dbf49-112">無。</span><span class="sxs-lookup"><span data-stu-id="dbf49-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbf49-113">子元素</span><span class="sxs-lookup"><span data-stu-id="dbf49-113">Child Elements</span></span>  
  
|<span data-ttu-id="dbf49-114">**Element**</span><span class="sxs-lookup"><span data-stu-id="dbf49-114">**Element**</span></span>|<span data-ttu-id="dbf49-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="dbf49-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dbf49-116">新增</span><span class="sxs-lookup"><span data-stu-id="dbf49-116">add</span></span>](add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="dbf49-117">將 IP 位址或 DNS 名稱添加到代理繞過清單中。</span><span class="sxs-lookup"><span data-stu-id="dbf49-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="dbf49-118">清楚</span><span class="sxs-lookup"><span data-stu-id="dbf49-118">clear</span></span>](clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="dbf49-119">清除旁路清單。</span><span class="sxs-lookup"><span data-stu-id="dbf49-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="dbf49-120">移除</span><span class="sxs-lookup"><span data-stu-id="dbf49-120">remove</span></span>](remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="dbf49-121">從代理繞過清單中刪除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="dbf49-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbf49-122">父項目</span><span class="sxs-lookup"><span data-stu-id="dbf49-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dbf49-123">**Element**</span><span class="sxs-lookup"><span data-stu-id="dbf49-123">**Element**</span></span>|<span data-ttu-id="dbf49-124">**描述**</span><span class="sxs-lookup"><span data-stu-id="dbf49-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dbf49-125">預設代理</span><span class="sxs-lookup"><span data-stu-id="dbf49-125">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="dbf49-126">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="dbf49-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbf49-127">備註</span><span class="sxs-lookup"><span data-stu-id="dbf49-127">Remarks</span></span>  
 <span data-ttu-id="dbf49-128">旁路清單包含常規運算式，用於描述<xref:System.Net.WebRequest>實例直接存取而不是通過代理伺服器訪問的 URI。</span><span class="sxs-lookup"><span data-stu-id="dbf49-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="dbf49-129">為此元素指定正則運算式時應小心謹慎。</span><span class="sxs-lookup"><span data-stu-id="dbf49-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="dbf49-130">正則運算式"[a-z].contoso\\\\.com"與contoso.com域中的任何主機匹配，但它也與contoso.com.cpandl.com域中的任何主機匹配。</span><span class="sxs-lookup"><span data-stu-id="dbf49-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="dbf49-131">要僅匹配contoso.com域中的主機，請使用錨點（"$"）："[a-z].contoso.com$"。\\ \\</span><span class="sxs-lookup"><span data-stu-id="dbf49-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="dbf49-132">有關正則運算式的詳細資訊，請參閱。[.NET 框架正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="dbf49-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dbf49-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="dbf49-133">Configuration Files</span></span>  
 <span data-ttu-id="dbf49-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="dbf49-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbf49-135">範例</span><span class="sxs-lookup"><span data-stu-id="dbf49-135">Example</span></span>  
 <span data-ttu-id="dbf49-136">下面的示例將兩個位址添加到旁路清單中。</span><span class="sxs-lookup"><span data-stu-id="dbf49-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="dbf49-137">第一個繞過contoso.com域中所有伺服器的代理;第二個伺服器繞過其 IP 位址以 192.168 開頭的所有伺服器的代理。</span><span class="sxs-lookup"><span data-stu-id="dbf49-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dbf49-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dbf49-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="dbf49-139">網路設置架構</span><span class="sxs-lookup"><span data-stu-id="dbf49-139">Network Settings Schema</span></span>](index.md)
