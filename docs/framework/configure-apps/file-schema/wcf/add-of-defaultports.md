---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926700"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="8fce0-102">\<新增 defaultPorts > \<的 ></span><span class="sxs-lookup"><span data-stu-id="8fce0-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="8fce0-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="8fce0-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="8fce0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8fce0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8fce0-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="8fce0-105">\<behaviors></span></span>  
<span data-ttu-id="8fce0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8fce0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8fce0-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="8fce0-107">\<behavior></span></span>  
<span data-ttu-id="8fce0-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="8fce0-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="8fce0-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="8fce0-109">\<defaultPorts></span></span>  
<span data-ttu-id="8fce0-110">\<add></span><span class="sxs-lookup"><span data-stu-id="8fce0-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fce0-111">語法</span><span class="sxs-lookup"><span data-stu-id="8fce0-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fce0-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8fce0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8fce0-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8fce0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fce0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8fce0-114">Attributes</span></span>  
  
|<span data-ttu-id="8fce0-115">屬性</span><span class="sxs-lookup"><span data-stu-id="8fce0-115">Attribute</span></span>|<span data-ttu-id="8fce0-116">描述</span><span class="sxs-lookup"><span data-stu-id="8fce0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8fce0-117">連接埠</span><span class="sxs-lookup"><span data-stu-id="8fce0-117">port</span></span>|<span data-ttu-id="8fce0-118">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="8fce0-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="8fce0-119">scheme</span><span class="sxs-lookup"><span data-stu-id="8fce0-119">scheme</span></span>|<span data-ttu-id="8fce0-120">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="8fce0-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fce0-121">子元素</span><span class="sxs-lookup"><span data-stu-id="8fce0-121">Child Elements</span></span>  
 <span data-ttu-id="8fce0-122">無。</span><span class="sxs-lookup"><span data-stu-id="8fce0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8fce0-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8fce0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8fce0-124">項目</span><span class="sxs-lookup"><span data-stu-id="8fce0-124">Element</span></span>|<span data-ttu-id="8fce0-125">描述</span><span class="sxs-lookup"><span data-stu-id="8fce0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fce0-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="8fce0-126">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="8fce0-127">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="8fce0-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fce0-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fce0-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
