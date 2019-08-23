---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936417"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="9590d-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="9590d-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="9590d-102">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="9590d-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="9590d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9590d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9590d-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="9590d-104">\<behaviors></span></span>  
<span data-ttu-id="9590d-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9590d-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="9590d-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="9590d-106">\<behavior></span></span>  
<span data-ttu-id="9590d-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="9590d-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9590d-108">語法</span><span class="sxs-lookup"><span data-stu-id="9590d-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9590d-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9590d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9590d-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9590d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9590d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9590d-111">Attributes</span></span>  
  
|<span data-ttu-id="9590d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9590d-112">Attribute</span></span>|<span data-ttu-id="9590d-113">說明</span><span class="sxs-lookup"><span data-stu-id="9590d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9590d-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="9590d-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="9590d-115">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="9590d-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9590d-116">子元素</span><span class="sxs-lookup"><span data-stu-id="9590d-116">Child Elements</span></span>  
 <span data-ttu-id="9590d-117">無。</span><span class="sxs-lookup"><span data-stu-id="9590d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9590d-118">父項目</span><span class="sxs-lookup"><span data-stu-id="9590d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9590d-119">項目</span><span class="sxs-lookup"><span data-stu-id="9590d-119">Element</span></span>|<span data-ttu-id="9590d-120">說明</span><span class="sxs-lookup"><span data-stu-id="9590d-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9590d-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9590d-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="9590d-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="9590d-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9590d-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9590d-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
