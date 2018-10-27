---
title: '&lt;移除&gt;bypasslist （網路設定） 的項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove elemment, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 80d8fc48141c0d23b93445bdfec02b95ba4a589f
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50032526"
---
# <a name="ltremovegt-element-for-bypasslist-network-settings"></a><span data-ttu-id="944b1-102">&lt;移除&gt;bypasslist （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="944b1-102">&lt;remove&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="944b1-103">Proxy 略過清單移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="944b1-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>  
  
 <span data-ttu-id="944b1-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="944b1-104">\<configuration></span></span>  
<span data-ttu-id="944b1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="944b1-105">\<system.net></span></span>  
<span data-ttu-id="944b1-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="944b1-106">\<defaultProxy></span></span>  
<span data-ttu-id="944b1-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="944b1-107">\<bypasslist></span></span>  
<span data-ttu-id="944b1-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="944b1-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="944b1-109">語法</span><span class="sxs-lookup"><span data-stu-id="944b1-109">Syntax</span></span>  
  
```xml  
<remove   
  address="regular expression"   
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="944b1-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="944b1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="944b1-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="944b1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="944b1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="944b1-112">Attributes</span></span>  
  
|<span data-ttu-id="944b1-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="944b1-113">**Attribute**</span></span>|<span data-ttu-id="944b1-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="944b1-114">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="944b1-115">描述 IP 位址或 DNS 名稱的規則運算式。</span><span class="sxs-lookup"><span data-stu-id="944b1-115">A regular expression describing an IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="944b1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="944b1-116">Child Elements</span></span>  
 <span data-ttu-id="944b1-117">無。</span><span class="sxs-lookup"><span data-stu-id="944b1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="944b1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="944b1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="944b1-119">**目**</span><span class="sxs-lookup"><span data-stu-id="944b1-119">**Element**</span></span>|<span data-ttu-id="944b1-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="944b1-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="944b1-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="944b1-121">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="944b1-122">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="944b1-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="944b1-123">備註</span><span class="sxs-lookup"><span data-stu-id="944b1-123">Remarks</span></span>  
 <span data-ttu-id="944b1-124">`remove`項目移除規則運算式描述 IP 位址或 DNS 伺服器名稱，從清單中的 略過 proxy 伺服器的位址。</span><span class="sxs-lookup"><span data-stu-id="944b1-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="944b1-125">位址先前已定義在組態檔中或在組態階層架構中較高層級。</span><span class="sxs-lookup"><span data-stu-id="944b1-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
 <span data-ttu-id="944b1-126">值`address`屬性應該是規則運算式描述一組 IP 位址或主機名稱。</span><span class="sxs-lookup"><span data-stu-id="944b1-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>  
  
 <span data-ttu-id="944b1-127">如需有關規則運算式的詳細資訊，請參閱。[.NET framework 規則運算式](../../../../../docs/standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="944b1-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../../docs/standard/base-types/regular-expressions.md).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="944b1-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="944b1-128">Configuration Files</span></span>  
 <span data-ttu-id="944b1-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="944b1-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="944b1-130">範例</span><span class="sxs-lookup"><span data-stu-id="944b1-130">Example</span></span>  
 <span data-ttu-id="944b1-131">下列範例會移除任何先前的定義，adventure-works.com 網域，然後略過清單中加入 contoso.com 網域。</span><span class="sxs-lookup"><span data-stu-id="944b1-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
        <remove address="[a-z]+\.adventure-works\.com$" />  
        <add address="[a-z]+\.contoso\.com$" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="944b1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="944b1-132">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="944b1-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="944b1-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
