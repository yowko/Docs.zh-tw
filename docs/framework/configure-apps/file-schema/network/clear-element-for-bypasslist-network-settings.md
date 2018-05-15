---
title: '&lt;清除&gt;bypasslist （網路設定） 的項目'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9297b68a31117aabfa45328954ccb9c7cdac66c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="3ed62-102">&lt;清除&gt;bypasslist （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="3ed62-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="3ed62-103">清除 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="3ed62-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="3ed62-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3ed62-104">\<configuration></span></span>  
<span data-ttu-id="3ed62-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3ed62-105">\<system.net></span></span>  
<span data-ttu-id="3ed62-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="3ed62-106">\<defaultProxy></span></span>  
<span data-ttu-id="3ed62-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="3ed62-107">\<bypasslist></span></span>  
<span data-ttu-id="3ed62-108">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="3ed62-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ed62-109">語法</span><span class="sxs-lookup"><span data-stu-id="3ed62-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ed62-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ed62-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ed62-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3ed62-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ed62-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3ed62-112">Attributes</span></span>  
 <span data-ttu-id="3ed62-113">無。</span><span class="sxs-lookup"><span data-stu-id="3ed62-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ed62-114">子項目</span><span class="sxs-lookup"><span data-stu-id="3ed62-114">Child Elements</span></span>  
 <span data-ttu-id="3ed62-115">無。</span><span class="sxs-lookup"><span data-stu-id="3ed62-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ed62-116">父項目</span><span class="sxs-lookup"><span data-stu-id="3ed62-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3ed62-117">**目**</span><span class="sxs-lookup"><span data-stu-id="3ed62-117">**Element**</span></span>|<span data-ttu-id="3ed62-118">**描述**</span><span class="sxs-lookup"><span data-stu-id="3ed62-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3ed62-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="3ed62-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="3ed62-120">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="3ed62-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ed62-121">備註</span><span class="sxs-lookup"><span data-stu-id="3ed62-121">Remarks</span></span>  
 <span data-ttu-id="3ed62-122">`clear`項目清除略過清單中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="3ed62-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3ed62-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="3ed62-123">Configuration Files</span></span>  
 <span data-ttu-id="3ed62-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="3ed62-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed62-125">範例</span><span class="sxs-lookup"><span data-stu-id="3ed62-125">Example</span></span>  
 <span data-ttu-id="3ed62-126">下列範例會清除 略過清單，並再將兩個位址加入至略過清單。</span><span class="sxs-lookup"><span data-stu-id="3ed62-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="3ed62-127">第一個略過 contoso.com 網域; 中的所有伺服器的 proxy第二個會略過的所有伺服器的 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="3ed62-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ed62-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ed62-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="3ed62-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3ed62-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
