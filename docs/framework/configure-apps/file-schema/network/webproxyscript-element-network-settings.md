---
title: "&lt;webProxyScript&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4c7d6154d354e806a04ccc9da062db64c534039b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="82591-102">&lt;webProxyScript&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="82591-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="82591-103">設定用來探索 Web proxy 的指令碼的特性。</span><span class="sxs-lookup"><span data-stu-id="82591-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="82591-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="82591-104">\<configuration></span></span>  
<span data-ttu-id="82591-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="82591-105">\<system.net></span></span>  
<span data-ttu-id="82591-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="82591-106">\<settings></span></span>  
<span data-ttu-id="82591-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="82591-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82591-108">語法</span><span class="sxs-lookup"><span data-stu-id="82591-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82591-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82591-109">Attributes and Elements</span></span>  
 <span data-ttu-id="82591-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="82591-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82591-111">屬性</span><span class="sxs-lookup"><span data-stu-id="82591-111">Attributes</span></span>  
  
|<span data-ttu-id="82591-112">屬性</span><span class="sxs-lookup"><span data-stu-id="82591-112">Attribute</span></span>|<span data-ttu-id="82591-113">描述</span><span class="sxs-lookup"><span data-stu-id="82591-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="82591-114">指定下載指令碼中小時、 分鐘和秒的最大時間。</span><span class="sxs-lookup"><span data-stu-id="82591-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="82591-115">預設值是一分鐘。</span><span class="sxs-lookup"><span data-stu-id="82591-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82591-116">子元素</span><span class="sxs-lookup"><span data-stu-id="82591-116">Child Elements</span></span>  
 <span data-ttu-id="82591-117">無。</span><span class="sxs-lookup"><span data-stu-id="82591-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82591-118">父項目</span><span class="sxs-lookup"><span data-stu-id="82591-118">Parent Elements</span></span>  
  
|<span data-ttu-id="82591-119">項目</span><span class="sxs-lookup"><span data-stu-id="82591-119">Element</span></span>|<span data-ttu-id="82591-120">描述</span><span class="sxs-lookup"><span data-stu-id="82591-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82591-121">設定</span><span class="sxs-lookup"><span data-stu-id="82591-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="82591-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="82591-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82591-123">備註</span><span class="sxs-lookup"><span data-stu-id="82591-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="82591-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="82591-124">Configuration Files</span></span>  
 <span data-ttu-id="82591-125">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="82591-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82591-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="82591-126">See Also</span></span>  
 [<span data-ttu-id="82591-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="82591-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
