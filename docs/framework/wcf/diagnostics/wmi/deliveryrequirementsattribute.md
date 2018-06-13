---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: d294ba4f14472012b9e311ee53742633b5173f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485776"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="80d5f-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="80d5f-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="80d5f-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="80d5f-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d5f-104">語法</span><span class="sxs-lookup"><span data-stu-id="80d5f-104">Syntax</span></span>  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="80d5f-105">方法</span><span class="sxs-lookup"><span data-stu-id="80d5f-105">Methods</span></span>  
 <span data-ttu-id="80d5f-106">DeliveryRequirementsAttribute 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="80d5f-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="80d5f-107">屬性</span><span class="sxs-lookup"><span data-stu-id="80d5f-107">Properties</span></span>  
 <span data-ttu-id="80d5f-108">DeliveryRequirementsAttribute 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="80d5f-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="80d5f-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="80d5f-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="80d5f-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="80d5f-110">Data type: string</span></span>  
  
 <span data-ttu-id="80d5f-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="80d5f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80d5f-112">指定服務的繫結是否支援合約。</span><span class="sxs-lookup"><span data-stu-id="80d5f-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="80d5f-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="80d5f-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="80d5f-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="80d5f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="80d5f-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="80d5f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80d5f-116">指定繫結是否支援已排序的訊息。</span><span class="sxs-lookup"><span data-stu-id="80d5f-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="80d5f-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="80d5f-117">TargetContract</span></span>  
 <span data-ttu-id="80d5f-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="80d5f-118">Data type: string</span></span>  
  
 <span data-ttu-id="80d5f-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="80d5f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="80d5f-120">它所套用的合約。</span><span class="sxs-lookup"><span data-stu-id="80d5f-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d5f-121">需求</span><span class="sxs-lookup"><span data-stu-id="80d5f-121">Requirements</span></span>  
  
|<span data-ttu-id="80d5f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="80d5f-122">MOF</span></span>|<span data-ttu-id="80d5f-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="80d5f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="80d5f-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="80d5f-124">Namespace</span></span>|<span data-ttu-id="80d5f-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="80d5f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="80d5f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80d5f-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
