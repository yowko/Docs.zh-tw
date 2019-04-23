---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136743"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="c81e0-102">\<新增 > 的\<a d d ></span><span class="sxs-lookup"><span data-stu-id="c81e0-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="c81e0-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="c81e0-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="c81e0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c81e0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c81e0-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c81e0-105">\<behaviors></span></span>  
<span data-ttu-id="c81e0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c81e0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c81e0-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c81e0-107">\<behavior></span></span>  
<span data-ttu-id="c81e0-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="c81e0-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="c81e0-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="c81e0-109">\<defaultPorts></span></span>  
<span data-ttu-id="c81e0-110">\<add></span><span class="sxs-lookup"><span data-stu-id="c81e0-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81e0-111">語法</span><span class="sxs-lookup"><span data-stu-id="c81e0-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c81e0-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c81e0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c81e0-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c81e0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c81e0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c81e0-114">Attributes</span></span>  
  
|<span data-ttu-id="c81e0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c81e0-115">Attribute</span></span>|<span data-ttu-id="c81e0-116">描述</span><span class="sxs-lookup"><span data-stu-id="c81e0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c81e0-117">連接埠</span><span class="sxs-lookup"><span data-stu-id="c81e0-117">port</span></span>|<span data-ttu-id="c81e0-118">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="c81e0-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="c81e0-119">scheme</span><span class="sxs-lookup"><span data-stu-id="c81e0-119">scheme</span></span>|<span data-ttu-id="c81e0-120">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="c81e0-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c81e0-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c81e0-121">Child Elements</span></span>  
 <span data-ttu-id="c81e0-122">無。</span><span class="sxs-lookup"><span data-stu-id="c81e0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c81e0-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c81e0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c81e0-124">項目</span><span class="sxs-lookup"><span data-stu-id="c81e0-124">Element</span></span>|<span data-ttu-id="c81e0-125">描述</span><span class="sxs-lookup"><span data-stu-id="c81e0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c81e0-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="c81e0-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="c81e0-127">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="c81e0-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c81e0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c81e0-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
