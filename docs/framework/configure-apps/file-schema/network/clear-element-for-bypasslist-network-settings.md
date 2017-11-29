---
title: "&lt;清除&gt;bypasslist （網路設定） 的項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/bypasslist/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, bypasslist
- <clear> element, bypasslist
- <bypasslist>, clear element
- bypasslist, clear element
ms.assetid: 301584ca-a914-4100-b180-3b288d3b099e
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5ee20b9177d519010c40351e335973dce10256f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcleargt-element-for-bypasslist-network-settings"></a><span data-ttu-id="6fd33-102">&lt;清除&gt;bypasslist （網路設定） 的項目</span><span class="sxs-lookup"><span data-stu-id="6fd33-102">&lt;clear&gt; Element for bypasslist (Network Settings)</span></span>
<span data-ttu-id="6fd33-103">清除 proxy 略過清單。</span><span class="sxs-lookup"><span data-stu-id="6fd33-103">Clears the proxy bypass list.</span></span>  
  
 <span data-ttu-id="6fd33-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6fd33-104">\<configuration></span></span>  
<span data-ttu-id="6fd33-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="6fd33-105">\<system.net></span></span>  
<span data-ttu-id="6fd33-106">\<defaultProxy ></span><span class="sxs-lookup"><span data-stu-id="6fd33-106">\<defaultProxy></span></span>  
<span data-ttu-id="6fd33-107">\<bypasslist ></span><span class="sxs-lookup"><span data-stu-id="6fd33-107">\<bypasslist></span></span>  
<span data-ttu-id="6fd33-108">\<清除 ></span><span class="sxs-lookup"><span data-stu-id="6fd33-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd33-109">語法</span><span class="sxs-lookup"><span data-stu-id="6fd33-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fd33-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6fd33-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6fd33-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6fd33-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fd33-112">屬性</span><span class="sxs-lookup"><span data-stu-id="6fd33-112">Attributes</span></span>  
 <span data-ttu-id="6fd33-113">無。</span><span class="sxs-lookup"><span data-stu-id="6fd33-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6fd33-114">子元素</span><span class="sxs-lookup"><span data-stu-id="6fd33-114">Child Elements</span></span>  
 <span data-ttu-id="6fd33-115">無。</span><span class="sxs-lookup"><span data-stu-id="6fd33-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fd33-116">父項目</span><span class="sxs-lookup"><span data-stu-id="6fd33-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6fd33-117">**目**</span><span class="sxs-lookup"><span data-stu-id="6fd33-117">**Element**</span></span>|<span data-ttu-id="6fd33-118">**說明**</span><span class="sxs-lookup"><span data-stu-id="6fd33-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6fd33-119">bypasslist</span><span class="sxs-lookup"><span data-stu-id="6fd33-119">bypasslist</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/bypasslist-element-network-settings.md)|<span data-ttu-id="6fd33-120">提供一組規則運算式，其中說明不使用 proxy 的位址。</span><span class="sxs-lookup"><span data-stu-id="6fd33-120">Provides a set of regular expressions that describe addresses that do not use a proxy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fd33-121">備註</span><span class="sxs-lookup"><span data-stu-id="6fd33-121">Remarks</span></span>  
 <span data-ttu-id="6fd33-122">`clear`項目清除略過清單中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6fd33-122">The `clear` element clears all entries from the bypass list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6fd33-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="6fd33-123">Configuration Files</span></span>  
 <span data-ttu-id="6fd33-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="6fd33-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fd33-125">範例</span><span class="sxs-lookup"><span data-stu-id="6fd33-125">Example</span></span>  
 <span data-ttu-id="6fd33-126">下列範例會清除 略過清單，並再將兩個位址加入至略過清單。</span><span class="sxs-lookup"><span data-stu-id="6fd33-126">The following example clears the bypass list and then adds two addresses to the bypass list.</span></span> <span data-ttu-id="6fd33-127">第一個略過 contoso.com 網域; 中的所有伺服器的 proxy第二個會略過的所有伺服器的 IP 位址 192.168 的 proxy。</span><span class="sxs-lookup"><span data-stu-id="6fd33-127">The first bypasses the proxy for all servers in the contoso.com domain; the second bypasses the proxy for all servers whose IP address begins with 192.168.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6fd33-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fd33-128">See Also</span></span>  
 <xref:System.Net.WebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="6fd33-129">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6fd33-129">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
