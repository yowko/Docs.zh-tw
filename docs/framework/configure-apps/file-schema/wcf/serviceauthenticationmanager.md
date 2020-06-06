---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399714"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="e2471-101">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="e2471-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="e2471-102">語法</span><span class="sxs-lookup"><span data-stu-id="e2471-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2471-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2471-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e2471-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2471-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2471-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e2471-105">Attributes</span></span>  
  
|<span data-ttu-id="e2471-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e2471-106">Attribute</span></span>|<span data-ttu-id="e2471-107">描述</span><span class="sxs-lookup"><span data-stu-id="e2471-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2471-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="e2471-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="e2471-109">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="e2471-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2471-110">子元素</span><span class="sxs-lookup"><span data-stu-id="e2471-110">Child Elements</span></span>  
 <span data-ttu-id="e2471-111">無。</span><span class="sxs-lookup"><span data-stu-id="e2471-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2471-112">父項目</span><span class="sxs-lookup"><span data-stu-id="e2471-112">Parent Elements</span></span>  
  
|<span data-ttu-id="e2471-113">元素</span><span class="sxs-lookup"><span data-stu-id="e2471-113">Element</span></span>|<span data-ttu-id="e2471-114">描述</span><span class="sxs-lookup"><span data-stu-id="e2471-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="e2471-115">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="e2471-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2471-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2471-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
