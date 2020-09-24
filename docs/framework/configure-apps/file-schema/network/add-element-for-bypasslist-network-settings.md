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
ms.openlocfilehash: 927a43f352fd776d9e6ba52ebea6ba2a1ccd4d48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149487"
---
# <a name="add-element-for-bypasslist-network-settings"></a><span data-ttu-id="2afc8-102">bypasslist 的 \<add> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="2afc8-102">\<add> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="2afc8-103">將 IP 位址或 DNS 名稱新增至 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="2afc8-103">Adds an IP address or DNS name to the proxy bypass list.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="2afc8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2afc8-104">Syntax</span></span>  
  
```xml  
<add
  address="regular expression"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2afc8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2afc8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="2afc8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2afc8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2afc8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="2afc8-107">Attributes</span></span>  
  
|<span data-ttu-id="2afc8-108">**Attribute**</span><span class="sxs-lookup"><span data-stu-id="2afc8-108">**Attribute**</span></span>|<span data-ttu-id="2afc8-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="2afc8-109">**Description**</span></span>|  
|-------------------|---------------------|  
|<span data-ttu-id="2afc8-110">**address**</span><span class="sxs-lookup"><span data-stu-id="2afc8-110">**address**</span></span>|<span data-ttu-id="2afc8-111">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="2afc8-111">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2afc8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2afc8-112">Child Elements</span></span>  

 <span data-ttu-id="2afc8-113">無。</span><span class="sxs-lookup"><span data-stu-id="2afc8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2afc8-114">父項目</span><span class="sxs-lookup"><span data-stu-id="2afc8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="2afc8-115">**Element**</span><span class="sxs-lookup"><span data-stu-id="2afc8-115">**Element**</span></span>|<span data-ttu-id="2afc8-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="2afc8-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2afc8-117">bypasslist</span><span class="sxs-lookup"><span data-stu-id="2afc8-117">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="2afc8-118">提供一組正則運算式，用來描述未使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="2afc8-118">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2afc8-119">備註</span><span class="sxs-lookup"><span data-stu-id="2afc8-119">Remarks</span></span>  

 <span data-ttu-id="2afc8-120">`add`元素會將描述 IP 位址或 DNS 伺服器名稱的正則運算式，插入至略過 proxy 伺服器的地址清單。</span><span class="sxs-lookup"><span data-stu-id="2afc8-120">The `add` element inserts regular expressions describing IP addresses or DNS server names to the list of addresses that bypass a proxy server.</span></span>  
  
 <span data-ttu-id="2afc8-121">屬性的值 `address` 應該是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="2afc8-121">The value of the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="2afc8-122">為此元素指定正則運算式時，請特別小心。</span><span class="sxs-lookup"><span data-stu-id="2afc8-122">You should use caution when specifying a regular expression for this element.</span></span> <span data-ttu-id="2afc8-123">正則運算式 "[a-z] + \\ . \\ .com" 符合 contoso.com 網域中的任何主機，但它也符合 contoso.com.cpandl.com 網域中的任何主機。</span><span class="sxs-lookup"><span data-stu-id="2afc8-123">The regular expression "[a-z]+\\.contoso\\.com" matches any host in the contoso.com domain, but it also matches any host in the contoso.com.cpandl.com domain.</span></span> <span data-ttu-id="2afc8-124">若只要比對 contoso.com 網域中的主機，請使用錨點 ( "$" ) ： "[a-z] + \\ . \\ .com $"。</span><span class="sxs-lookup"><span data-stu-id="2afc8-124">To match only a host in the contoso.com domain, use an anchor ("$"): "[a-z]+\\.contoso\\.com$".</span></span>  
  
 <span data-ttu-id="2afc8-125">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="2afc8-125">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2afc8-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="2afc8-126">Configuration Files</span></span>  

 <span data-ttu-id="2afc8-127">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="2afc8-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2afc8-128">範例</span><span class="sxs-lookup"><span data-stu-id="2afc8-128">Example</span></span>  

 <span data-ttu-id="2afc8-129">下列範例會將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="2afc8-129">The following example adds two addresses to the bypass list.</span></span> <span data-ttu-id="2afc8-130">第一個會針對 contoso.com 網域中的所有伺服器略過 proxy;第二個會針對 IP 位址開頭為192.168 的所有伺服器略過 proxy。</span><span class="sxs-lookup"><span data-stu-id="2afc8-130">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2afc8-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2afc8-131">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="2afc8-132">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2afc8-132">Network Settings Schema</span></span>](index.md)
