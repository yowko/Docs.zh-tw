---
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 5e772e23b21c566c906be854e33b924698dcf3e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158704"
---
# \<privacyNoticeAt>

<span data-ttu-id="f08f1-101">表示組態項目，指定用於 `wsFederationHttp` 繫結中的隱私權注意事項。</span><span class="sxs-lookup"><span data-stu-id="f08f1-101">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="f08f1-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="f08f1-102">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="f08f1-103">類型</span><span class="sxs-lookup"><span data-stu-id="f08f1-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f08f1-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f08f1-104">Attributes and Elements</span></span>  

 <span data-ttu-id="f08f1-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f08f1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f08f1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f08f1-106">Attributes</span></span>  
  
|<span data-ttu-id="f08f1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f08f1-107">Attribute</span></span>|<span data-ttu-id="f08f1-108">描述</span><span class="sxs-lookup"><span data-stu-id="f08f1-108">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="f08f1-109">指定隱私權注意事項所在之 URI 的字串。</span><span class="sxs-lookup"><span data-stu-id="f08f1-109">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="f08f1-110">指定這個隱私權注意事項版本的整數。</span><span class="sxs-lookup"><span data-stu-id="f08f1-110">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f08f1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="f08f1-111">Child Elements</span></span>  

 <span data-ttu-id="f08f1-112">無。</span><span class="sxs-lookup"><span data-stu-id="f08f1-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f08f1-113">父項目</span><span class="sxs-lookup"><span data-stu-id="f08f1-113">Parent Elements</span></span>  
  
|<span data-ttu-id="f08f1-114">項目</span><span class="sxs-lookup"><span data-stu-id="f08f1-114">Element</span></span>|<span data-ttu-id="f08f1-115">描述</span><span class="sxs-lookup"><span data-stu-id="f08f1-115">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="f08f1-116">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="f08f1-116">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f08f1-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f08f1-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f08f1-118">繫結</span><span class="sxs-lookup"><span data-stu-id="f08f1-118">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f08f1-119">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="f08f1-119">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f08f1-120">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="f08f1-120">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
