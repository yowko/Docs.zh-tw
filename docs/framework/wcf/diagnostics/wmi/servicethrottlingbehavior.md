---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771763"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="852ca-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="852ca-102">ServiceThrottlingBehavior</span></span>
<span data-ttu-id="852ca-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="852ca-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="852ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="852ca-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="852ca-105">方法</span><span class="sxs-lookup"><span data-stu-id="852ca-105">Methods</span></span>  
 <span data-ttu-id="852ca-106">ServiceThrottlingBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="852ca-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="852ca-107">屬性</span><span class="sxs-lookup"><span data-stu-id="852ca-107">Properties</span></span>  
 <span data-ttu-id="852ca-108">ServiceThrottlingBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="852ca-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="852ca-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="852ca-109">MaxConcurrentCalls</span></span>  
 <span data-ttu-id="852ca-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="852ca-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="852ca-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="852ca-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="852ca-112">在 ServiceHost 中的所有發送器物件上主動處理的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="852ca-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="852ca-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="852ca-113">MaxConcurrentInstances</span></span>  
 <span data-ttu-id="852ca-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="852ca-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="852ca-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="852ca-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="852ca-116">一次可執行的服務物件數目上限。</span><span class="sxs-lookup"><span data-stu-id="852ca-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="852ca-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="852ca-117">MaxConcurrentSessions</span></span>  
 <span data-ttu-id="852ca-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="852ca-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="852ca-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="852ca-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="852ca-120">主機一次可接受的工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="852ca-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="852ca-121">需求</span><span class="sxs-lookup"><span data-stu-id="852ca-121">Requirements</span></span>  
  
|<span data-ttu-id="852ca-122">MOF</span><span class="sxs-lookup"><span data-stu-id="852ca-122">MOF</span></span>|<span data-ttu-id="852ca-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="852ca-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="852ca-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="852ca-124">Namespace</span></span>|<span data-ttu-id="852ca-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="852ca-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="852ca-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="852ca-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
