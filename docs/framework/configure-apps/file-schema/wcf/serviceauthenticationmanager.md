---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670374"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="5b6c1-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="5b6c1-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="5b6c1-102">提供工作流程組態項目，這個項目會在服務層級建立傳輸、訊息或建立者的有效性。</span><span class="sxs-lookup"><span data-stu-id="5b6c1-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="5b6c1-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5b6c1-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5b6c1-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="5b6c1-104">\<behaviors></span></span>  
<span data-ttu-id="5b6c1-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5b6c1-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="5b6c1-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5b6c1-106">\<behavior></span></span>  
<span data-ttu-id="5b6c1-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="5b6c1-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6c1-108">語法</span><span class="sxs-lookup"><span data-stu-id="5b6c1-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b6c1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5b6c1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5b6c1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5b6c1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b6c1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5b6c1-111">Attributes</span></span>  
  
|<span data-ttu-id="5b6c1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5b6c1-112">Attribute</span></span>|<span data-ttu-id="5b6c1-113">描述</span><span class="sxs-lookup"><span data-stu-id="5b6c1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5b6c1-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="5b6c1-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="5b6c1-115">字串，指定目前行為的驗證原則類型。</span><span class="sxs-lookup"><span data-stu-id="5b6c1-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b6c1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5b6c1-116">Child Elements</span></span>  
 <span data-ttu-id="5b6c1-117">無。</span><span class="sxs-lookup"><span data-stu-id="5b6c1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b6c1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5b6c1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5b6c1-119">項目</span><span class="sxs-lookup"><span data-stu-id="5b6c1-119">Element</span></span>|<span data-ttu-id="5b6c1-120">描述</span><span class="sxs-lookup"><span data-stu-id="5b6c1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5b6c1-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5b6c1-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5b6c1-122">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="5b6c1-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5b6c1-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b6c1-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
