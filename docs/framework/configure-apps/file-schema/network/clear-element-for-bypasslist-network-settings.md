---
title: bypasslist 的 <clear> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
ms.openlocfilehash: 4d078dac14103560423bfccdd4a1717031e7a60f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699504"
---
# <a name="clear-element-for-bypasslist-network-settings"></a><span data-ttu-id="e6b48-102">適用于 bypasslist 的 @no__t 0clear > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="e6b48-102">\<clear> Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="e6b48-103">清除 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="e6b48-103">Clears the proxy bypass list.</span></span>  
  
[<span data-ttu-id="e6b48-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e6b48-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e6b48-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6b48-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="e6b48-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6b48-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>  
<span data-ttu-id="e6b48-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<bypasslist >** ](bypasslist-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e6b48-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bypasslist>**](bypasslist-element-network-settings.md)</span></span>  
<span data-ttu-id="e6b48-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="e6b48-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b48-109">語法</span><span class="sxs-lookup"><span data-stu-id="e6b48-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6b48-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6b48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6b48-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e6b48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6b48-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e6b48-112">Attributes</span></span>  
 <span data-ttu-id="e6b48-113">無。</span><span class="sxs-lookup"><span data-stu-id="e6b48-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e6b48-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e6b48-114">Child Elements</span></span>  
 <span data-ttu-id="e6b48-115">無。</span><span class="sxs-lookup"><span data-stu-id="e6b48-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6b48-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e6b48-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e6b48-117">**目**</span><span class="sxs-lookup"><span data-stu-id="e6b48-117">**Element**</span></span>|<span data-ttu-id="e6b48-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="e6b48-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e6b48-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="e6b48-119">bypasslist</span></span>](bypasslist-element-network-settings.md)|<span data-ttu-id="e6b48-120">提供一組正則運算式，描述不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="e6b48-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b48-121">備註</span><span class="sxs-lookup"><span data-stu-id="e6b48-121">Remarks</span></span>  
 <span data-ttu-id="e6b48-122">@No__t-0 元素會清除略過清單中的所有專案。</span><span class="sxs-lookup"><span data-stu-id="e6b48-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e6b48-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="e6b48-123">Configuration Files</span></span>  
 <span data-ttu-id="e6b48-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="e6b48-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6b48-125">範例</span><span class="sxs-lookup"><span data-stu-id="e6b48-125">Example</span></span>  
 <span data-ttu-id="e6b48-126">下列範例會清除略過清單，然後將兩個位址新增至略過清單。</span><span class="sxs-lookup"><span data-stu-id="e6b48-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="e6b48-127">第一個會略過 contoso.com 網域中所有伺服器的 proxy;第二個會略過其 IP 位址開頭為192.168 的所有伺服器的 proxy。</span><span class="sxs-lookup"><span data-stu-id="e6b48-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <bypasslist>  
         <clear/>  
        <add address="[a-z]+\.contoso\.com$" />  
        <add address="192\.168\.\d{1,3}\.\d{1,3}" />  
      </bypasslist>  
    </defaultProxy>  
  </system.net>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="e6b48-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6b48-128">See also</span></span>

- <xref:System.Net.WebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="e6b48-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="e6b48-129">Network Settings Schema</span></span>](index.md)
