---
title: "&lt;bypasslist&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3d349f14535de806e0b130ef64b58333e63f1b86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltbypasslistgt-element-network-settings"></a><span data-ttu-id="062f2-102">&lt;bypasslist&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="062f2-102">&lt;bypasslist&gt; Element (Network Settings)</span></span>
<span data-ttu-id="062f2-103">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="062f2-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="062f2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="062f2-104">\<configuration></span></span>  
<span data-ttu-id="062f2-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="062f2-105">\<system.net></span></span>  
<span data-ttu-id="062f2-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="062f2-106">\<defaultProxy></span></span>  
<span data-ttu-id="062f2-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="062f2-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="062f2-108">語法</span><span class="sxs-lookup"><span data-stu-id="062f2-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="062f2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="062f2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="062f2-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="062f2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="062f2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="062f2-111">Attributes</span></span>  
 <span data-ttu-id="062f2-112">無。</span><span class="sxs-lookup"><span data-stu-id="062f2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="062f2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="062f2-113">Child Elements</span></span>  
  
|<span data-ttu-id="062f2-114">**目**</span><span class="sxs-lookup"><span data-stu-id="062f2-114">**Element**</span></span>|<span data-ttu-id="062f2-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="062f2-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="062f2-116">add</span><span class="sxs-lookup"><span data-stu-id="062f2-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="062f2-117">將 proxy 略過清單中的 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="062f2-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="062f2-118">clear</span><span class="sxs-lookup"><span data-stu-id="062f2-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="062f2-119">清除 略過清單。</span><span class="sxs-lookup"><span data-stu-id="062f2-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="062f2-120">remove</span><span class="sxs-lookup"><span data-stu-id="062f2-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="062f2-121">Proxy 略過清單移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="062f2-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="062f2-122">父項目</span><span class="sxs-lookup"><span data-stu-id="062f2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="062f2-123">**目**</span><span class="sxs-lookup"><span data-stu-id="062f2-123">**Element**</span></span>|<span data-ttu-id="062f2-124">**說明**</span><span class="sxs-lookup"><span data-stu-id="062f2-124">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="062f2-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="062f2-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="062f2-126">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="062f2-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="062f2-127">備註</span><span class="sxs-lookup"><span data-stu-id="062f2-127">Remarks</span></span>  
 <span data-ttu-id="062f2-128">略過清單包含說明 Uri 的規則運算式的<xref:System.Net.WebRequest>執行個體直接而不是透過 proxy 伺服器存取。</span><span class="sxs-lookup"><span data-stu-id="062f2-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="062f2-129">指定此元素的規則運算式時，您應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="062f2-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="062f2-130">規則運算式"[a 到 z] +\\.contoso\\.com"比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="062f2-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="062f2-131">要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a 到 z] +\\.contoso\\.com$"。</span><span class="sxs-lookup"><span data-stu-id="062f2-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="062f2-132">如需規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="062f2-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="062f2-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="062f2-133">Configuration Files</span></span>  
 <span data-ttu-id="062f2-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="062f2-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="062f2-135">範例</span><span class="sxs-lookup"><span data-stu-id="062f2-135">Example</span></span>  
 <span data-ttu-id="062f2-136">下列範例會將兩個位址加入至略過清單。</span><span class="sxs-lookup"><span data-stu-id="062f2-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="062f2-137">第一個略過 contoso.com 網域; 中的所有伺服器的 proxy第二個會略過的所有伺服器開始其 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="062f2-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="062f2-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="062f2-138">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="062f2-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="062f2-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
