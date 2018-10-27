---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: 7bfc03299fffc8070a7d8a4b3885706ea861bdf6
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/26/2018
ms.locfileid: "50042892"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="39beb-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="39beb-102">DeliveryRequirementsAttribute</span></span>
<span data-ttu-id="39beb-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="39beb-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39beb-104">語法</span><span class="sxs-lookup"><span data-stu-id="39beb-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="39beb-105">方法</span><span class="sxs-lookup"><span data-stu-id="39beb-105">Methods</span></span>  
 <span data-ttu-id="39beb-106">DeliveryRequirementsAttribute 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="39beb-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="39beb-107">屬性</span><span class="sxs-lookup"><span data-stu-id="39beb-107">Properties</span></span>  
 <span data-ttu-id="39beb-108">DeliveryRequirementsAttribute 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="39beb-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="39beb-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="39beb-109">QueuedDeliveryRequirements</span></span>  
 <span data-ttu-id="39beb-110">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="39beb-110">Data type: string</span></span>  
  
 <span data-ttu-id="39beb-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="39beb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39beb-112">指定服務的繫結是否支援合約。</span><span class="sxs-lookup"><span data-stu-id="39beb-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="39beb-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="39beb-113">RequireOrderedDelivery</span></span>  
 <span data-ttu-id="39beb-114">資料型別：布林值</span><span class="sxs-lookup"><span data-stu-id="39beb-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="39beb-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="39beb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39beb-116">指定繫結是否支援已排序的訊息。</span><span class="sxs-lookup"><span data-stu-id="39beb-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="39beb-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="39beb-117">TargetContract</span></span>  
 <span data-ttu-id="39beb-118">資料型別：字串</span><span class="sxs-lookup"><span data-stu-id="39beb-118">Data type: string</span></span>  
  
 <span data-ttu-id="39beb-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="39beb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39beb-120">它所套用的合約。</span><span class="sxs-lookup"><span data-stu-id="39beb-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39beb-121">需求</span><span class="sxs-lookup"><span data-stu-id="39beb-121">Requirements</span></span>  
  
|<span data-ttu-id="39beb-122">MOF</span><span class="sxs-lookup"><span data-stu-id="39beb-122">MOF</span></span>|<span data-ttu-id="39beb-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="39beb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="39beb-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="39beb-124">Namespace</span></span>|<span data-ttu-id="39beb-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="39beb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39beb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39beb-126">See Also</span></span>  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
