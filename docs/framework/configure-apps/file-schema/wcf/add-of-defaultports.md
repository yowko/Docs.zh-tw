---
title: '&lt;defaultPorts&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 28ddc98bd66c1f74f857448aa710d3998ddbd3dc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748746"
---
# <a name="ltaddgt-of-ltdefaultportsgt"></a><span data-ttu-id="75b23-102">&lt;defaultPorts&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="75b23-102">&lt;add&gt; of &lt;defaultPorts&gt;</span></span>
<span data-ttu-id="75b23-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="75b23-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="75b23-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="75b23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75b23-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="75b23-105">\<behaviors></span></span>  
<span data-ttu-id="75b23-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="75b23-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="75b23-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="75b23-107">\<behavior></span></span>  
<span data-ttu-id="75b23-108">\<useRequestHeadersForMetadataAddress ></span><span class="sxs-lookup"><span data-stu-id="75b23-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="75b23-109">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="75b23-109">\<defaultPorts></span></span>  
<span data-ttu-id="75b23-110">\<add></span><span class="sxs-lookup"><span data-stu-id="75b23-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b23-111">語法</span><span class="sxs-lookup"><span data-stu-id="75b23-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>   <defaultPorts>      <add port="Integer" scheme="String" />   </defaultPorts></useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75b23-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="75b23-112">Attributes and Elements</span></span>  
 <span data-ttu-id="75b23-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="75b23-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75b23-114">屬性</span><span class="sxs-lookup"><span data-stu-id="75b23-114">Attributes</span></span>  
  
|<span data-ttu-id="75b23-115">屬性</span><span class="sxs-lookup"><span data-stu-id="75b23-115">Attribute</span></span>|<span data-ttu-id="75b23-116">描述</span><span class="sxs-lookup"><span data-stu-id="75b23-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75b23-117">連接埠</span><span class="sxs-lookup"><span data-stu-id="75b23-117">port</span></span>|<span data-ttu-id="75b23-118">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="75b23-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="75b23-119">scheme</span><span class="sxs-lookup"><span data-stu-id="75b23-119">scheme</span></span>|<span data-ttu-id="75b23-120">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="75b23-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75b23-121">子項目</span><span class="sxs-lookup"><span data-stu-id="75b23-121">Child Elements</span></span>  
 <span data-ttu-id="75b23-122">無。</span><span class="sxs-lookup"><span data-stu-id="75b23-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75b23-123">父項目</span><span class="sxs-lookup"><span data-stu-id="75b23-123">Parent Elements</span></span>  
  
|<span data-ttu-id="75b23-124">項目</span><span class="sxs-lookup"><span data-stu-id="75b23-124">Element</span></span>|<span data-ttu-id="75b23-125">描述</span><span class="sxs-lookup"><span data-stu-id="75b23-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b23-126">\<a d d ></span><span class="sxs-lookup"><span data-stu-id="75b23-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="75b23-127">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="75b23-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75b23-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75b23-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DefaultPortElement>
