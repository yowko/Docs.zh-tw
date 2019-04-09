---
title: <bypasslist> 項目 （網路設定）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bypasslist
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist
helpviewer_keywords:
- bypasslist element
- <bypasslist> element
ms.assetid: 124446b7-abb1-4e5e-a492-b64398f268f1
ms.openlocfilehash: d3d986dae478f49504dae21b9f39574b7887b4d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202218"
---
# <a name="bypasslist-element-network-settings"></a><span data-ttu-id="472c1-102">\<bypasslist > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="472c1-102">\<bypasslist> Element (Network Settings)</span></span>
<span data-ttu-id="472c1-103">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="472c1-103">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>  
  
 <span data-ttu-id="472c1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="472c1-104">\<configuration></span></span>  
<span data-ttu-id="472c1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="472c1-105">\<system.net></span></span>  
<span data-ttu-id="472c1-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="472c1-106">\<defaultProxy></span></span>  
<span data-ttu-id="472c1-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="472c1-107">\<bypasslist></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="472c1-108">語法</span><span class="sxs-lookup"><span data-stu-id="472c1-108">Syntax</span></span>  
  
```xml  
<bypasslist>   
</bypasslist>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="472c1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="472c1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="472c1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="472c1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="472c1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="472c1-111">Attributes</span></span>  
 <span data-ttu-id="472c1-112">無。</span><span class="sxs-lookup"><span data-stu-id="472c1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="472c1-113">子元素</span><span class="sxs-lookup"><span data-stu-id="472c1-113">Child Elements</span></span>  
  
|**<span data-ttu-id="472c1-114">項目</span><span class="sxs-lookup"><span data-stu-id="472c1-114">Element</span></span>**|**<span data-ttu-id="472c1-115">描述</span><span class="sxs-lookup"><span data-stu-id="472c1-115">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="472c1-116">add</span><span class="sxs-lookup"><span data-stu-id="472c1-116">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-bypasslist-network-settings.md)|<span data-ttu-id="472c1-117">將 IP 位址或 DNS 名稱加入至 proxy 略過清單中。</span><span class="sxs-lookup"><span data-stu-id="472c1-117">Adds an IP address or DNS name to the proxy bypass list.</span></span>|  
|[<span data-ttu-id="472c1-118">清除</span><span class="sxs-lookup"><span data-stu-id="472c1-118">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-bypasslist-network-settings.md)|<span data-ttu-id="472c1-119">清除 略過清單。</span><span class="sxs-lookup"><span data-stu-id="472c1-119">Clears the bypass list.</span></span>|  
|[<span data-ttu-id="472c1-120">remove</span><span class="sxs-lookup"><span data-stu-id="472c1-120">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-bypasslist-network-settings.md)|<span data-ttu-id="472c1-121">Proxy 略過清單移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="472c1-121">Removes an IP address or DNS name from the proxy bypass list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="472c1-122">父項目</span><span class="sxs-lookup"><span data-stu-id="472c1-122">Parent Elements</span></span>  
  
|**<span data-ttu-id="472c1-123">項目</span><span class="sxs-lookup"><span data-stu-id="472c1-123">Element</span></span>**|**<span data-ttu-id="472c1-124">描述</span><span class="sxs-lookup"><span data-stu-id="472c1-124">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="472c1-125">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="472c1-125">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="472c1-126">設定超文字傳輸協定 (HTTP) 的 Proxy 伺服器。</span><span class="sxs-lookup"><span data-stu-id="472c1-126">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="472c1-127">備註</span><span class="sxs-lookup"><span data-stu-id="472c1-127">Remarks</span></span>  
 <span data-ttu-id="472c1-128">略過清單包含說明 Uri 的規則運算式，<xref:System.Net.WebRequest>執行個體直接而不是透過 proxy 伺服器存取。</span><span class="sxs-lookup"><span data-stu-id="472c1-128">The bypass list contains regular expressions that describe URIs that <xref:System.Net.WebRequest> instances access directly instead of through the proxy server.</span></span>  
  
 <span data-ttu-id="472c1-129">指定這個項目的規則運算式時，您應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="472c1-129">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="472c1-130">規則運算式"[a-z]、[0-9]、[_] +\\.contoso\\.com 」 比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="472c1-130">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="472c1-131">若要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a-z]、[0-9]、[_] +\\.contoso\\.com$"。</span><span class="sxs-lookup"><span data-stu-id="472c1-131">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="472c1-132">如需有關規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="472c1-132">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="472c1-133">組態檔</span><span class="sxs-lookup"><span data-stu-id="472c1-133">Configuration Files</span></span>  
 <span data-ttu-id="472c1-134">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="472c1-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="472c1-135">範例</span><span class="sxs-lookup"><span data-stu-id="472c1-135">Example</span></span>  
 <span data-ttu-id="472c1-136">下列範例會將略過清單中的兩個位址。</span><span class="sxs-lookup"><span data-stu-id="472c1-136">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="472c1-137">第一個會略過在 contoso.com 網域中的所有伺服器的 proxy第二個會略過的所有伺服器開始其 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="472c1-137">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP addresses begin with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="472c1-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="472c1-138">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="472c1-139">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="472c1-139">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
