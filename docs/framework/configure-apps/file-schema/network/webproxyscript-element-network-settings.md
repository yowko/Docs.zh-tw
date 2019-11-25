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
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089067"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="7edb7-102">\<webProxyScript > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="7edb7-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="7edb7-103">設定用來探索 Web proxy 之腳本的特性。</span><span class="sxs-lookup"><span data-stu-id="7edb7-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

<span data-ttu-id="7edb7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7edb7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7edb7-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7edb7-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="7edb7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<設定 >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7edb7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="7edb7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="7edb7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7edb7-108">語法</span><span class="sxs-lookup"><span data-stu-id="7edb7-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7edb7-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7edb7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7edb7-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7edb7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7edb7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7edb7-111">Attributes</span></span>  
  
|<span data-ttu-id="7edb7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7edb7-112">Attribute</span></span>|<span data-ttu-id="7edb7-113">描述</span><span class="sxs-lookup"><span data-stu-id="7edb7-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="7edb7-114">指定下載腳本的時間上限，以小時、分鐘和秒為單位。</span><span class="sxs-lookup"><span data-stu-id="7edb7-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="7edb7-115">預設值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="7edb7-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7edb7-116">子項目</span><span class="sxs-lookup"><span data-stu-id="7edb7-116">Child Elements</span></span>  
 <span data-ttu-id="7edb7-117">無。</span><span class="sxs-lookup"><span data-stu-id="7edb7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7edb7-118">父項目</span><span class="sxs-lookup"><span data-stu-id="7edb7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="7edb7-119">項目</span><span class="sxs-lookup"><span data-stu-id="7edb7-119">Element</span></span>|<span data-ttu-id="7edb7-120">描述</span><span class="sxs-lookup"><span data-stu-id="7edb7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7edb7-121">設置</span><span class="sxs-lookup"><span data-stu-id="7edb7-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7edb7-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="7edb7-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7edb7-123">備註</span><span class="sxs-lookup"><span data-stu-id="7edb7-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7edb7-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="7edb7-124">Configuration Files</span></span>  
 <span data-ttu-id="7edb7-125">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="7edb7-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7edb7-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="7edb7-126">See also</span></span>

- [<span data-ttu-id="7edb7-127">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7edb7-127">Network Settings Schema</span></span>](index.md)
