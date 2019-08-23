---
title: bypasslist 的 <remove> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- <bypasslist>, remove element
- remove element, bypasslist
- bypasslist, remove element
- remove element, bypasslist
ms.assetid: 61dcfb4a-e3d9-4abf-a2cd-7d685fe2f64b
ms.openlocfilehash: 99c18bd5b779845d52831b4a9591eaf4d5e5530b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920955"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="036e6-102">\<移除 bypasslist 的 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="036e6-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="036e6-103">從 proxy 略過清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="036e6-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

<span data-ttu-id="036e6-104">\<configuration > </span><span class="sxs-lookup"><span data-stu-id="036e6-104">\<configuration></span></span>\
<span data-ttu-id="036e6-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="036e6-105">\<system.net></span></span>\
<span data-ttu-id="036e6-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="036e6-106">\<defaultProxy></span></span>\
<span data-ttu-id="036e6-107">\<bypasslist></span><span class="sxs-lookup"><span data-stu-id="036e6-107">\<bypasslist></span></span>\
<span data-ttu-id="036e6-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="036e6-108">\<remove></span></span>

## <a name="syntax"></a><span data-ttu-id="036e6-109">語法</span><span class="sxs-lookup"><span data-stu-id="036e6-109">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="036e6-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="036e6-110">Attributes and Elements</span></span>

<span data-ttu-id="036e6-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="036e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="036e6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="036e6-112">Attributes</span></span>

|<span data-ttu-id="036e6-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="036e6-113">**Attribute**</span></span>|<span data-ttu-id="036e6-114">**描述**</span><span class="sxs-lookup"><span data-stu-id="036e6-114">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="036e6-115">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="036e6-115">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="036e6-116">子元素</span><span class="sxs-lookup"><span data-stu-id="036e6-116">Child Elements</span></span>

<span data-ttu-id="036e6-117">無。</span><span class="sxs-lookup"><span data-stu-id="036e6-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="036e6-118">父項目</span><span class="sxs-lookup"><span data-stu-id="036e6-118">Parent Elements</span></span>

|<span data-ttu-id="036e6-119">**目**</span><span class="sxs-lookup"><span data-stu-id="036e6-119">**Element**</span></span>|<span data-ttu-id="036e6-120">**描述**</span><span class="sxs-lookup"><span data-stu-id="036e6-120">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="036e6-121">bypasslist</span><span class="sxs-lookup"><span data-stu-id="036e6-121">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="036e6-122">提供一組正則運算式, 描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="036e6-122">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="036e6-123">備註</span><span class="sxs-lookup"><span data-stu-id="036e6-123">Remarks</span></span>

<span data-ttu-id="036e6-124">`remove`元素會從略過 proxy 伺服器的地址清單中, 移除描述 IP 位址或 DNS 伺服器名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="036e6-124">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="036e6-125">先前已在設定檔或設定階層的較高層級定義位址。</span><span class="sxs-lookup"><span data-stu-id="036e6-125">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="036e6-126">`address`屬性的值應該是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="036e6-126">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="036e6-127">如需正則運算式的詳細資訊, 請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="036e6-127">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="036e6-128">組態檔</span><span class="sxs-lookup"><span data-stu-id="036e6-128">Configuration Files</span></span>

<span data-ttu-id="036e6-129">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="036e6-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="036e6-130">範例</span><span class="sxs-lookup"><span data-stu-id="036e6-130">Example</span></span>

<span data-ttu-id="036e6-131">下列範例會移除 adventure-works.com 網域的任何先前定義, 然後將 contoso.com 網域新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="036e6-131">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="036e6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="036e6-132">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="036e6-133">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="036e6-133">Network Settings Schema</span></span>](index.md)
