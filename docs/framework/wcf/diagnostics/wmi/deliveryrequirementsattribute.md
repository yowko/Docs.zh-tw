---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="6c9ec-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="6c9ec-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="6c9ec-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="6c9ec-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c9ec-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6c9ec-105">方法</span><span class="sxs-lookup"><span data-stu-id="6c9ec-105">Methods</span></span>  
 <span data-ttu-id="6c9ec-106">DeliveryRequirementsAttribute 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="6c9ec-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6c9ec-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6c9ec-107">Properties</span></span>  
 <span data-ttu-id="6c9ec-108">DeliveryRequirementsAttribute 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="6c9ec-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="6c9ec-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="6c9ec-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="6c9ec-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6c9ec-110">Data type: string</span></span>  
  
 <span data-ttu-id="6c9ec-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c9ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c9ec-112">指定服務的繫結是否支援合約。</span><span class="sxs-lookup"><span data-stu-id="6c9ec-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="6c9ec-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="6c9ec-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="6c9ec-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="6c9ec-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6c9ec-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c9ec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c9ec-116">指定繫結是否支援已排序的訊息。</span><span class="sxs-lookup"><span data-stu-id="6c9ec-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="6c9ec-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="6c9ec-117">TargetContract</span></span>  
 <span data-ttu-id="6c9ec-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="6c9ec-118">Data type: string</span></span>  
  
 <span data-ttu-id="6c9ec-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="6c9ec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6c9ec-120">它所套用的合約。</span><span class="sxs-lookup"><span data-stu-id="6c9ec-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c9ec-121">需求</span><span class="sxs-lookup"><span data-stu-id="6c9ec-121">Requirements</span></span>  
  
|<span data-ttu-id="6c9ec-122">MOF</span><span class="sxs-lookup"><span data-stu-id="6c9ec-122">MOF</span></span>|<span data-ttu-id="6c9ec-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="6c9ec-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6c9ec-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="6c9ec-124">Namespace</span></span>|<span data-ttu-id="6c9ec-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="6c9ec-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6c9ec-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c9ec-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
