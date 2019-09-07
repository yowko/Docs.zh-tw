---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399714"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="bd47d-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="bd47d-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="bd47d-102">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="bd47d-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="bd47d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bd47d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd47d-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bd47d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bd47d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd47d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bd47d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd47d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bd47d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bd47d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bd47d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<r >**</span><span class="sxs-lookup"><span data-stu-id="bd47d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd47d-109">語法</span><span class="sxs-lookup"><span data-stu-id="bd47d-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd47d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd47d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd47d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bd47d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd47d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bd47d-112">Attributes</span></span>  
  
|<span data-ttu-id="bd47d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bd47d-113">Attribute</span></span>|<span data-ttu-id="bd47d-114">描述</span><span class="sxs-lookup"><span data-stu-id="bd47d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd47d-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="bd47d-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="bd47d-116">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="bd47d-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd47d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="bd47d-117">Child Elements</span></span>  
 <span data-ttu-id="bd47d-118">無。</span><span class="sxs-lookup"><span data-stu-id="bd47d-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd47d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bd47d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bd47d-120">項目</span><span class="sxs-lookup"><span data-stu-id="bd47d-120">Element</span></span>|<span data-ttu-id="bd47d-121">描述</span><span class="sxs-lookup"><span data-stu-id="bd47d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd47d-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bd47d-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bd47d-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="bd47d-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd47d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd47d-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
