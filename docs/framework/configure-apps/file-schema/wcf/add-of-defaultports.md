---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261591"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="c745f-102">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="c745f-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="c745f-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="c745f-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="c745f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c745f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c745f-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c745f-105">\<behaviors></span></span>  
<span data-ttu-id="c745f-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c745f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c745f-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c745f-107">\<behavior></span></span>  
<span data-ttu-id="c745f-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="c745f-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="c745f-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="c745f-109">\<defaultPorts></span></span>  
<span data-ttu-id="c745f-110">\<add></span><span class="sxs-lookup"><span data-stu-id="c745f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c745f-111">語法</span><span class="sxs-lookup"><span data-stu-id="c745f-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c745f-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c745f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c745f-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c745f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c745f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c745f-114">Attributes</span></span>  
  
|<span data-ttu-id="c745f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c745f-115">Attribute</span></span>|<span data-ttu-id="c745f-116">描述</span><span class="sxs-lookup"><span data-stu-id="c745f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c745f-117">連接埠</span><span class="sxs-lookup"><span data-stu-id="c745f-117">port</span></span>|<span data-ttu-id="c745f-118">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="c745f-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="c745f-119">scheme</span><span class="sxs-lookup"><span data-stu-id="c745f-119">scheme</span></span>|<span data-ttu-id="c745f-120">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="c745f-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c745f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c745f-121">Child Elements</span></span>  
 <span data-ttu-id="c745f-122">無。</span><span class="sxs-lookup"><span data-stu-id="c745f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c745f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c745f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c745f-124">項目</span><span class="sxs-lookup"><span data-stu-id="c745f-124">Element</span></span>|<span data-ttu-id="c745f-125">描述</span><span class="sxs-lookup"><span data-stu-id="c745f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c745f-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="c745f-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="c745f-127">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="c745f-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c745f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c745f-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
