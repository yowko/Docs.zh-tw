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
ms.openlocfilehash: e36b470b1ec348085b13a58630b0ac6833e43946
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178303"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="eeef8-102">\<webProxyScript> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="eeef8-102">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="eeef8-103">設定用來探索 Web proxy 的腳本特性。</span><span class="sxs-lookup"><span data-stu-id="eeef8-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="eeef8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="eeef8-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eeef8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eeef8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="eeef8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eeef8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eeef8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="eeef8-107">Attributes</span></span>  
  
|<span data-ttu-id="eeef8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="eeef8-108">Attribute</span></span>|<span data-ttu-id="eeef8-109">描述</span><span class="sxs-lookup"><span data-stu-id="eeef8-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="eeef8-110">指定下載腳本的最長時間（以小時、分鐘和秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="eeef8-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="eeef8-111">預設值為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="eeef8-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eeef8-112">子元素</span><span class="sxs-lookup"><span data-stu-id="eeef8-112">Child Elements</span></span>  

 <span data-ttu-id="eeef8-113">無。</span><span class="sxs-lookup"><span data-stu-id="eeef8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eeef8-114">父項目</span><span class="sxs-lookup"><span data-stu-id="eeef8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="eeef8-115">項目</span><span class="sxs-lookup"><span data-stu-id="eeef8-115">Element</span></span>|<span data-ttu-id="eeef8-116">描述</span><span class="sxs-lookup"><span data-stu-id="eeef8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eeef8-117">設定</span><span class="sxs-lookup"><span data-stu-id="eeef8-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="eeef8-118">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="eeef8-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeef8-119">備註</span><span class="sxs-lookup"><span data-stu-id="eeef8-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eeef8-120">組態檔</span><span class="sxs-lookup"><span data-stu-id="eeef8-120">Configuration Files</span></span>  

 <span data-ttu-id="eeef8-121">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="eeef8-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeef8-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eeef8-122">See also</span></span>

- [<span data-ttu-id="eeef8-123">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="eeef8-123">Network Settings Schema</span></span>](index.md)
