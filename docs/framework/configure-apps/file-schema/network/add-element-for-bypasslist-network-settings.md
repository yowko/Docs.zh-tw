---
title: "&lt;新增&gt;bypasslist （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <bypasslist>, add element
- bypasslist, add element
- <add> element, bypasslist
- add element, bypasslist
ms.assetid: a0b86e28-86b4-4497-abe8-d5fd614c7926
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bed3abd5522b748a2bd24ba03c7be5d991deae9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-bypasslist-network-settings"></a><span data-ttu-id="39420-102">&lt;新增&gt;bypasslist （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="39420-102">&lt;add&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="39420-103">將 proxy 略過清單中的 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="39420-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="39420-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="39420-104">\<configuration></span></span>  
<span data-ttu-id="39420-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="39420-105">\<system.net></span></span>  
<span data-ttu-id="39420-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="39420-106">\<defaultProxy></span></span>  
<span data-ttu-id="39420-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="39420-107">\<bypasslist></span></span>  
<span data-ttu-id="39420-108">\<add></span><span class="sxs-lookup"><span data-stu-id="39420-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39420-109">語法</span><span class="sxs-lookup"><span data-stu-id="39420-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39420-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="39420-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39420-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="39420-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39420-112">屬性</span><span class="sxs-lookup"><span data-stu-id="39420-112">Attributes</span></span>  
  
|<span data-ttu-id="39420-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="39420-113">**Attribute**</span></span>|<span data-ttu-id="39420-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="39420-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="39420-115">**address**</span><span class="sxs-lookup"><span data-stu-id="39420-115">**address**</span></span>|<span data-ttu-id="39420-116">描述 IP 位址或 DNS 名稱的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="39420-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39420-117">子元素</span><span class="sxs-lookup"><span data-stu-id="39420-117">Child Elements</span></span>  
 <span data-ttu-id="39420-118">無。</span><span class="sxs-lookup"><span data-stu-id="39420-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39420-119">父項目</span><span class="sxs-lookup"><span data-stu-id="39420-119">Parent Elements</span></span>  
  
|<span data-ttu-id="39420-120">**目**</span><span class="sxs-lookup"><span data-stu-id="39420-120">**Element**</span></span>|<span data-ttu-id="39420-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="39420-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="39420-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="39420-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="39420-123">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="39420-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39420-124">備註</span><span class="sxs-lookup"><span data-stu-id="39420-124">Remarks</span></span>  
 <span data-ttu-id="39420-125">`add`項目會插入規則運算式描述 IP 位址或 DNS 伺服器名稱略過 proxy 伺服器的位址清單。</span><span class="sxs-lookup"><span data-stu-id="39420-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="39420-126">值`address`屬性應該是規則運算式描述一組 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="39420-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="39420-127">指定此元素的規則運算式時，您應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="39420-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="39420-128">規則運算式"[a 到 z] +\\.contoso\\.com"比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="39420-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="39420-129">要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a 到 z] +\\.contoso\\.com$"。</span><span class="sxs-lookup"><span data-stu-id="39420-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="39420-130">如需規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="39420-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="39420-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="39420-131">Configuration Files</span></span>  
 <span data-ttu-id="39420-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="39420-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39420-133">範例</span><span class="sxs-lookup"><span data-stu-id="39420-133">Example</span></span>  
 <span data-ttu-id="39420-134">下列範例會將兩個位址加入至略過清單。</span><span class="sxs-lookup"><span data-stu-id="39420-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="39420-135">第一個略過 contoso.com 網域; 中的所有伺服器的 proxy第二個會略過的所有伺服器的 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="39420-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="39420-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="39420-136">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="39420-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="39420-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
