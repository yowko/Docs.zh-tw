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
ms.openlocfilehash: 904c8e23f7a09a975a6f3b9322ed6bc4148d9ba4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674659"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="f11dc-102">\<新增 > bypasslist （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="f11dc-102">\<add> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="f11dc-103">將 IP 位址或 DNS 名稱加入至 proxy 略過清單中。</span><span class="sxs-lookup"><span data-stu-id="f11dc-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
 <span data-ttu-id="f11dc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f11dc-104">\<configuration></span></span>  
<span data-ttu-id="f11dc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f11dc-105">\<system.net></span></span>  
<span data-ttu-id="f11dc-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="f11dc-106">\<defaultProxy></span></span>  
<span data-ttu-id="f11dc-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="f11dc-107">\<bypasslist></span></span>  
<span data-ttu-id="f11dc-108">\<add></span><span class="sxs-lookup"><span data-stu-id="f11dc-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11dc-109">語法</span><span class="sxs-lookup"><span data-stu-id="f11dc-109">Syntax</span></span>  
  
```xml  
<add   
  address="regular expression"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f11dc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f11dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f11dc-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f11dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f11dc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f11dc-112">Attributes</span></span>  
  
|<span data-ttu-id="f11dc-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f11dc-113">**Attribute**</span></span>|<span data-ttu-id="f11dc-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="f11dc-114">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="f11dc-115">**address**</span><span class="sxs-lookup"><span data-stu-id="f11dc-115">**address**</span></span>|<span data-ttu-id="f11dc-116">描述 IP 位址或 DNS 名稱的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="f11dc-116">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f11dc-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f11dc-117">Child Elements</span></span>  
 <span data-ttu-id="f11dc-118">無。</span><span class="sxs-lookup"><span data-stu-id="f11dc-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f11dc-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f11dc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f11dc-120">**目**</span><span class="sxs-lookup"><span data-stu-id="f11dc-120">**Element**</span></span>|<span data-ttu-id="f11dc-121">**描述**</span><span class="sxs-lookup"><span data-stu-id="f11dc-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f11dc-122">bypasslist</span><span class="sxs-lookup"><span data-stu-id="f11dc-122">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="f11dc-123">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="f11dc-123">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f11dc-124">備註</span><span class="sxs-lookup"><span data-stu-id="f11dc-124">Remarks</span></span>  
 <span data-ttu-id="f11dc-125">`add`項目會插入描述 IP 位址或 DNS 伺服器名稱略過 proxy 伺服器的位址清單的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="f11dc-125">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="f11dc-126">值`address`屬性應該是規則運算式描述一組 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="f11dc-126">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="f11dc-127">指定這個項目的規則運算式時，您應謹慎小心。</span><span class="sxs-lookup"><span data-stu-id="f11dc-127">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="f11dc-128">規則運算式"[a-z]、[0-9]、[_] +\\.contoso\\.com 」 比對任何裝載在 contoso.com 網域，但它也會比對 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="f11dc-128">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="f11dc-129">若要比對 contoso.com 網域中的主機，使用錨點 （"$"）:"[a-z]、[0-9]、[_] +\\.contoso\\.com$"。</span><span class="sxs-lookup"><span data-stu-id="f11dc-129">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="f11dc-130">如需有關規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f11dc-130">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f11dc-131">組態檔</span><span class="sxs-lookup"><span data-stu-id="f11dc-131">Configuration Files</span></span>  
 <span data-ttu-id="f11dc-132">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="f11dc-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f11dc-133">範例</span><span class="sxs-lookup"><span data-stu-id="f11dc-133">Example</span></span>  
 <span data-ttu-id="f11dc-134">下列範例會將略過清單中的兩個位址。</span><span class="sxs-lookup"><span data-stu-id="f11dc-134">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="f11dc-135">第一個會略過在 contoso.com 網域中的所有伺服器的 proxy第二個會略過的所有伺服器會開始其 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="f11dc-135">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f11dc-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11dc-136">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="f11dc-137">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f11dc-137">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
