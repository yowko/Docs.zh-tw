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
ms.openlocfilehash: 97b49a8a520d6a4f72945366874991d2deb18710
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697899"
---
# <a name="remove-element-for-bypasslist-network-settings"></a><span data-ttu-id="1b1fb-102">bypasslist 的 \<remove> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="1b1fb-102">\<remove> Element for bypasslist (Network Settings)</span></span>

<span data-ttu-id="1b1fb-103">從 proxy 略過清單中移除 IP 位址或 DNS 名稱。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-103">Removes an IP address or DNS name from the proxy bypass list.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  

## <a name="syntax"></a><span data-ttu-id="1b1fb-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b1fb-104">Syntax</span></span>

```xml
<remove
  address="regular expression"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b1fb-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b1fb-105">Attributes and Elements</span></span>

<span data-ttu-id="1b1fb-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b1fb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1b1fb-107">Attributes</span></span>

|<span data-ttu-id="1b1fb-108">**屬性**</span><span class="sxs-lookup"><span data-stu-id="1b1fb-108">**Attribute**</span></span>|<span data-ttu-id="1b1fb-109">**說明**</span><span class="sxs-lookup"><span data-stu-id="1b1fb-109">**Description**</span></span>|
|-------------------|---------------------|
|`address`|<span data-ttu-id="1b1fb-110">描述 IP 位址或 DNS 名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-110">A regular expression describing an IP address or DNS name.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="1b1fb-111">子元素</span><span class="sxs-lookup"><span data-stu-id="1b1fb-111">Child Elements</span></span>

<span data-ttu-id="1b1fb-112">無。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b1fb-113">父項目</span><span class="sxs-lookup"><span data-stu-id="1b1fb-113">Parent Elements</span></span>

|<span data-ttu-id="1b1fb-114">**元素**</span><span class="sxs-lookup"><span data-stu-id="1b1fb-114">**Element**</span></span>|<span data-ttu-id="1b1fb-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="1b1fb-115">**Description**</span></span>|
|-----------------|---------------------|
|[<span data-ttu-id="1b1fb-116">bypasslist</span><span class="sxs-lookup"><span data-stu-id="1b1fb-116">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="1b1fb-117">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-117">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1b1fb-118">備註</span><span class="sxs-lookup"><span data-stu-id="1b1fb-118">Remarks</span></span>

<span data-ttu-id="1b1fb-119">`remove`元素會從略過 proxy 伺服器的地址清單中，移除描述 IP 位址或 DNS 伺服器名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-119">The `remove` element removes regular expressions describing IP addresses or DNS server names from the list of addresses that bypass a proxy server.</span></span> <span data-ttu-id="1b1fb-120">先前已在設定檔或設定階層的較高層級定義位址。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-120">The addresses were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>

<span data-ttu-id="1b1fb-121">屬性的值 `address` 應該是描述一組 IP 位址或主機名稱的正則運算式。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-121">The value for the `address` attribute should be a regular expression that describes a set of IP addresses or host names.</span></span>

<span data-ttu-id="1b1fb-122">如需正則運算式的詳細資訊，請參閱。[.NET Framework 正則運算式](../../../../standard/base-types/regular-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-122">For more information about regular expressions, see .[.NET Framework Regular Expressions](../../../../standard/base-types/regular-expressions.md).</span></span>

## <a name="configuration-files"></a><span data-ttu-id="1b1fb-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="1b1fb-123">Configuration Files</span></span>

<span data-ttu-id="1b1fb-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="1b1fb-125">範例</span><span class="sxs-lookup"><span data-stu-id="1b1fb-125">Example</span></span>

<span data-ttu-id="1b1fb-126">下列範例會移除 adventure-works.com 網域的任何先前定義，然後將 contoso.com 網域新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="1b1fb-126">The following example removes any previous definition for the adventure-works.com domain, and then adds the contoso.com domain to the bypass list.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1b1fb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b1fb-127">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="1b1fb-128">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="1b1fb-128">Network Settings Schema</span></span>](index.md)
