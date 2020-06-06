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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089067"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="d40fe-102">\<webProxyScript> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d40fe-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="d40fe-103">設定用來探索 Web proxy 之腳本的特性。</span><span class="sxs-lookup"><span data-stu-id="d40fe-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="d40fe-104">語法</span><span class="sxs-lookup"><span data-stu-id="d40fe-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d40fe-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d40fe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d40fe-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d40fe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d40fe-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d40fe-107">Attributes</span></span>  
  
|<span data-ttu-id="d40fe-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d40fe-108">Attribute</span></span>|<span data-ttu-id="d40fe-109">描述</span><span class="sxs-lookup"><span data-stu-id="d40fe-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="d40fe-110">指定下載腳本的時間上限，以小時、分鐘和秒為單位。</span><span class="sxs-lookup"><span data-stu-id="d40fe-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="d40fe-111">預設值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="d40fe-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d40fe-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d40fe-112">Child Elements</span></span>  
 <span data-ttu-id="d40fe-113">無。</span><span class="sxs-lookup"><span data-stu-id="d40fe-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d40fe-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d40fe-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d40fe-115">元素</span><span class="sxs-lookup"><span data-stu-id="d40fe-115">Element</span></span>|<span data-ttu-id="d40fe-116">描述</span><span class="sxs-lookup"><span data-stu-id="d40fe-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d40fe-117">設定</span><span class="sxs-lookup"><span data-stu-id="d40fe-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="d40fe-118">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="d40fe-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d40fe-119">備註</span><span class="sxs-lookup"><span data-stu-id="d40fe-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d40fe-120">組態檔</span><span class="sxs-lookup"><span data-stu-id="d40fe-120">Configuration Files</span></span>  
 <span data-ttu-id="d40fe-121">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d40fe-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40fe-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d40fe-122">See also</span></span>

- [<span data-ttu-id="d40fe-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d40fe-123">Network Settings Schema</span></span>](index.md)
