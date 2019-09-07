---
title: <add> 的 <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400645"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="628fc-102">\<新增 defaultPorts > \<的 ></span><span class="sxs-lookup"><span data-stu-id="628fc-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="628fc-103">預設通訊端點，用戶端應用程式會接聽這個端點。</span><span class="sxs-lookup"><span data-stu-id="628fc-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="628fc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="628fc-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="628fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="628fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="628fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="628fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="628fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultPorts >** ](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="628fc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="628fc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="628fc-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="628fc-112">語法</span><span class="sxs-lookup"><span data-stu-id="628fc-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="628fc-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="628fc-113">Attributes and Elements</span></span>  
 <span data-ttu-id="628fc-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="628fc-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="628fc-115">屬性</span><span class="sxs-lookup"><span data-stu-id="628fc-115">Attributes</span></span>  
  
|<span data-ttu-id="628fc-116">屬性</span><span class="sxs-lookup"><span data-stu-id="628fc-116">Attribute</span></span>|<span data-ttu-id="628fc-117">描述</span><span class="sxs-lookup"><span data-stu-id="628fc-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="628fc-118">連接埠</span><span class="sxs-lookup"><span data-stu-id="628fc-118">port</span></span>|<span data-ttu-id="628fc-119">指定預設通訊埠編號的整數。</span><span class="sxs-lookup"><span data-stu-id="628fc-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="628fc-120">scheme</span><span class="sxs-lookup"><span data-stu-id="628fc-120">scheme</span></span>|<span data-ttu-id="628fc-121">指定與通訊連接埠相關之通訊協定設定群組的字串。</span><span class="sxs-lookup"><span data-stu-id="628fc-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="628fc-122">子元素</span><span class="sxs-lookup"><span data-stu-id="628fc-122">Child Elements</span></span>  
 <span data-ttu-id="628fc-123">無。</span><span class="sxs-lookup"><span data-stu-id="628fc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="628fc-124">父項目</span><span class="sxs-lookup"><span data-stu-id="628fc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="628fc-125">項目</span><span class="sxs-lookup"><span data-stu-id="628fc-125">Element</span></span>|<span data-ttu-id="628fc-126">描述</span><span class="sxs-lookup"><span data-stu-id="628fc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="628fc-127">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="628fc-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="628fc-128">預設連接埠的集合，這些連接埠會接聽用戶端應用程式所接聽的預設通訊端點。</span><span class="sxs-lookup"><span data-stu-id="628fc-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="628fc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="628fc-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
