---
title: '&lt;webProxyScript&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1e1450d2df424b32aacc5c113b5936001f65915a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47085632"
---
# <a name="ltwebproxyscriptgt-element-network-settings"></a><span data-ttu-id="d4418-102">&lt;webProxyScript&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="d4418-102">&lt;webProxyScript&gt; Element (Network Settings)</span></span>
<span data-ttu-id="d4418-103">設定用來探索 Web proxy 指令碼的特性。</span><span class="sxs-lookup"><span data-stu-id="d4418-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="d4418-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d4418-104">\<configuration></span></span>  
<span data-ttu-id="d4418-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d4418-105">\<system.net></span></span>  
<span data-ttu-id="d4418-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="d4418-106">\<settings></span></span>  
<span data-ttu-id="d4418-107">\<webProxyScript ></span><span class="sxs-lookup"><span data-stu-id="d4418-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4418-108">語法</span><span class="sxs-lookup"><span data-stu-id="d4418-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4418-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d4418-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d4418-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d4418-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4418-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d4418-111">Attributes</span></span>  
  
|<span data-ttu-id="d4418-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d4418-112">Attribute</span></span>|<span data-ttu-id="d4418-113">描述</span><span class="sxs-lookup"><span data-stu-id="d4418-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="d4418-114">指定下載指令碼中時數、 分鐘和秒鐘的時間上限。</span><span class="sxs-lookup"><span data-stu-id="d4418-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="d4418-115">預設值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="d4418-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4418-116">子元素</span><span class="sxs-lookup"><span data-stu-id="d4418-116">Child Elements</span></span>  
 <span data-ttu-id="d4418-117">無。</span><span class="sxs-lookup"><span data-stu-id="d4418-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4418-118">父項目</span><span class="sxs-lookup"><span data-stu-id="d4418-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d4418-119">項目</span><span class="sxs-lookup"><span data-stu-id="d4418-119">Element</span></span>|<span data-ttu-id="d4418-120">描述</span><span class="sxs-lookup"><span data-stu-id="d4418-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4418-121">設定</span><span class="sxs-lookup"><span data-stu-id="d4418-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="d4418-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="d4418-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4418-123">備註</span><span class="sxs-lookup"><span data-stu-id="d4418-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d4418-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="d4418-124">Configuration Files</span></span>  
 <span data-ttu-id="d4418-125">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d4418-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4418-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4418-126">See Also</span></span>  
 [<span data-ttu-id="d4418-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d4418-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
