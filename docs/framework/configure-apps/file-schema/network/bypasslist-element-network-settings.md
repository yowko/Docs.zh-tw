---
title: '&lt;bypasslist&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d2076ee5e95ab722fe828ee625392671a6281c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743897"
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="937a8-102">&lt;bypasslist&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="937a8-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="937a8-103">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="937a8-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="937a8-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="937a8-104">\<configuration></span></span>  
<span data-ttu-id="937a8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="937a8-105">\<system.net></span></span>  
<span data-ttu-id="937a8-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="937a8-106">\<defaultProxy></span></span>  
<span data-ttu-id="937a8-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="937a8-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="937a8-108">語法</span><span class="sxs-lookup"><span data-stu-id="937a8-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="937a8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="937a8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="937a8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="937a8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="937a8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="937a8-111">Attributes</span></span>  
 <span data-ttu-id="937a8-112">無。</span><span class="sxs-lookup"><span data-stu-id="937a8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="937a8-113">子項目</span><span class="sxs-lookup"><span data-stu-id="937a8-113">Child Elements</span></span>  
  
|<span data-ttu-id="937a8-114">**目**</span><span class="sxs-lookup"><span data-stu-id="937a8-114">**Element**</span></span>|<span data-ttu-id="937a8-115">**描述**</span><span class="sxs-lookup"><span data-stu-id="937a8-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="937a8-116">add</span><span class="sxs-lookup"><span data-stu-id="937a8-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="937a8-117">將 proxy 略過清單中的 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="937a8-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="937a8-118">clear</span><span class="sxs-lookup"><span data-stu-id="937a8-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="937a8-119">清除 略過清單。</span><span class="sxs-lookup"><span data-stu-id="937a8-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="937a8-120">remove</span><span class="sxs-lookup"><span data-stu-id="937a8-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="937a8-121">Proxy 略過清單移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="937a8-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="937a8-122">父項目</span><span class="sxs-lookup"><span data-stu-id="937a8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="937a8-123">**目**</span><span class="sxs-lookup"><span data-stu-id="937a8-123">**Element**</span></span>|<span data-ttu-id="937a8-124">**描述**</span><span class="sxs-lookup"><span data-stu-id="937a8-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="937a8-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="937a8-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="937a8-126">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="937a8-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="937a8-127">備註</span><span class="sxs-lookup"><span data-stu-id="937a8-127">Remarks</span></span>  
 <span data-ttu-id="937a8-128">略過清單包含說明 Uri 的規則運算式的<xref:System.Net.WebRequest>執行個體直接而不是透過 proxy 伺服器存取。</span><span class="sxs-lookup"><span data-stu-id="937a8-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="937a8-129">指定此元素的規則運算式時，您應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="937a8-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="937a8-130">規則運算式"[a 到 z] +\\.contoso\\.com"比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="937a8-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="937a8-131">要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a 到 z] +\\.contoso\\.com$"。</span><span class="sxs-lookup"><span data-stu-id="937a8-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="937a8-132">如需規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="937a8-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="937a8-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="937a8-133">Configuration Files</span></span>  
 <span data-ttu-id="937a8-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="937a8-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="937a8-135">範例</span><span class="sxs-lookup"><span data-stu-id="937a8-135">Example</span></span>  
 <span data-ttu-id="937a8-136">下列範例會將兩個位址加入至略過清單。</span><span class="sxs-lookup"><span data-stu-id="937a8-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="937a8-137">第一個略過 contoso.com 網域; 中的所有伺服器的 proxy第二個會略過的所有伺服器開始其 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="937a8-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="937a8-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="937a8-138">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="937a8-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="937a8-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
