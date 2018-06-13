---
title: '&lt;privacyNoticeAt&gt;'
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2914a3716b9e2adb6ebc47fd73ccee027a3b65da
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749240"
---
# <a name="ltprivacynoticeatgt"></a><span data-ttu-id="10d86-102">&lt;privacyNoticeAt&gt;</span><span class="sxs-lookup"><span data-stu-id="10d86-102">&lt;privacyNoticeAt&gt;</span></span>
<span data-ttu-id="10d86-103">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="10d86-103">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
 <span data-ttu-id="10d86-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="10d86-104">\<system.serviceModel></span></span>  
<span data-ttu-id="10d86-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="10d86-105">\<bindings></span></span>  
<span data-ttu-id="10d86-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="10d86-106">\<customBinding></span></span>  
<span data-ttu-id="10d86-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="10d86-107">\<binding></span></span>  
<span data-ttu-id="10d86-108">\<privacyNotice ></span><span class="sxs-lookup"><span data-stu-id="10d86-108">\<privacyNotice></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10d86-109">語法</span><span class="sxs-lookup"><span data-stu-id="10d86-109">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"  
        version="Integer" />  
```  
  
## <a name="type"></a><span data-ttu-id="10d86-110">類型</span><span class="sxs-lookup"><span data-stu-id="10d86-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10d86-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="10d86-111">Attributes and Elements</span></span>  
 <span data-ttu-id="10d86-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="10d86-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10d86-113">屬性</span><span class="sxs-lookup"><span data-stu-id="10d86-113">Attributes</span></span>  
  
|<span data-ttu-id="10d86-114">屬性</span><span class="sxs-lookup"><span data-stu-id="10d86-114">Attribute</span></span>|<span data-ttu-id="10d86-115">描述</span><span class="sxs-lookup"><span data-stu-id="10d86-115">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="10d86-116">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="10d86-116">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="10d86-117">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="10d86-117">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10d86-118">子項目</span><span class="sxs-lookup"><span data-stu-id="10d86-118">Child Elements</span></span>  
 <span data-ttu-id="10d86-119">無。</span><span class="sxs-lookup"><span data-stu-id="10d86-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10d86-120">父項目</span><span class="sxs-lookup"><span data-stu-id="10d86-120">Parent Elements</span></span>  
  
|<span data-ttu-id="10d86-121">項目</span><span class="sxs-lookup"><span data-stu-id="10d86-121">Element</span></span>|<span data-ttu-id="10d86-122">描述</span><span class="sxs-lookup"><span data-stu-id="10d86-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10d86-123">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="10d86-123">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="10d86-124">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="10d86-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10d86-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10d86-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="10d86-126">繫結</span><span class="sxs-lookup"><span data-stu-id="10d86-126">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="10d86-127">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="10d86-127">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="10d86-128">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="10d86-128">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="10d86-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="10d86-129">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
