---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: a7c1e06c74bd3ba62d52ef833b8ffb6a8fd594fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167167"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="9de56-101">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="9de56-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="9de56-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="9de56-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9de56-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9de56-103">Attributes and Elements</span></span>  

 <span data-ttu-id="9de56-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9de56-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9de56-105">屬性</span><span class="sxs-lookup"><span data-stu-id="9de56-105">Attributes</span></span>  
  
|<span data-ttu-id="9de56-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9de56-106">Attribute</span></span>|<span data-ttu-id="9de56-107">描述</span><span class="sxs-lookup"><span data-stu-id="9de56-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9de56-108">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="9de56-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="9de56-109">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="9de56-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9de56-110">子元素</span><span class="sxs-lookup"><span data-stu-id="9de56-110">Child Elements</span></span>  

 <span data-ttu-id="9de56-111">無。</span><span class="sxs-lookup"><span data-stu-id="9de56-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9de56-112">父項目</span><span class="sxs-lookup"><span data-stu-id="9de56-112">Parent Elements</span></span>  
  
|<span data-ttu-id="9de56-113">項目</span><span class="sxs-lookup"><span data-stu-id="9de56-113">Element</span></span>|<span data-ttu-id="9de56-114">描述</span><span class="sxs-lookup"><span data-stu-id="9de56-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9de56-115">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="9de56-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9de56-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9de56-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
