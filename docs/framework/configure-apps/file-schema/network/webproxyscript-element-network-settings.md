---
title: <webProxyScript> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659038"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="38de9-102">\<webProxyScript > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="38de9-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="38de9-103">設定用來探索 Web proxy 之腳本的特性。</span><span class="sxs-lookup"><span data-stu-id="38de9-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="38de9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="38de9-104">\<configuration></span></span>  
<span data-ttu-id="38de9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="38de9-105">\<system.net></span></span>  
<span data-ttu-id="38de9-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="38de9-106">\<settings></span></span>  
<span data-ttu-id="38de9-107">\<webProxyScript></span><span class="sxs-lookup"><span data-stu-id="38de9-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38de9-108">語法</span><span class="sxs-lookup"><span data-stu-id="38de9-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38de9-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38de9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="38de9-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="38de9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38de9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="38de9-111">Attributes</span></span>  
  
|<span data-ttu-id="38de9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="38de9-112">Attribute</span></span>|<span data-ttu-id="38de9-113">說明</span><span class="sxs-lookup"><span data-stu-id="38de9-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="38de9-114">指定下載腳本的時間上限, 以小時、分鐘和秒為單位。</span><span class="sxs-lookup"><span data-stu-id="38de9-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="38de9-115">預設值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="38de9-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38de9-116">子元素</span><span class="sxs-lookup"><span data-stu-id="38de9-116">Child Elements</span></span>  
 <span data-ttu-id="38de9-117">無。</span><span class="sxs-lookup"><span data-stu-id="38de9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38de9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="38de9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="38de9-119">項目</span><span class="sxs-lookup"><span data-stu-id="38de9-119">Element</span></span>|<span data-ttu-id="38de9-120">說明</span><span class="sxs-lookup"><span data-stu-id="38de9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38de9-121">設置</span><span class="sxs-lookup"><span data-stu-id="38de9-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="38de9-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="38de9-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38de9-123">備註</span><span class="sxs-lookup"><span data-stu-id="38de9-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="38de9-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="38de9-124">Configuration Files</span></span>  
 <span data-ttu-id="38de9-125">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="38de9-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38de9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38de9-126">See also</span></span>

- [<span data-ttu-id="38de9-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="38de9-127">Network Settings Schema</span></span>](index.md)
