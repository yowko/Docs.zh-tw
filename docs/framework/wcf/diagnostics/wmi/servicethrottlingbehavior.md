---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273980"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="1a482-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="1a482-102">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="1a482-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="1a482-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a482-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a482-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1a482-105">方法</span><span class="sxs-lookup"><span data-stu-id="1a482-105">Methods</span></span>  

 <span data-ttu-id="1a482-106">ServiceThrottlingBehavior 類別不會定義任何方法。</span><span class="sxs-lookup"><span data-stu-id="1a482-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1a482-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1a482-107">Properties</span></span>  

 <span data-ttu-id="1a482-108">ServiceThrottlingBehavior 類別具有下列屬性：</span><span class="sxs-lookup"><span data-stu-id="1a482-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="1a482-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="1a482-109">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="1a482-110">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="1a482-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1a482-111">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1a482-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a482-112">在 ServiceHost 中的所有發送器物件上主動處理的訊息數目上限。</span><span class="sxs-lookup"><span data-stu-id="1a482-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="1a482-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="1a482-113">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="1a482-114">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="1a482-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1a482-115">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1a482-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a482-116">一次可執行的服務物件數目上限。</span><span class="sxs-lookup"><span data-stu-id="1a482-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="1a482-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="1a482-117">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="1a482-118">資料型別：sint32</span><span class="sxs-lookup"><span data-stu-id="1a482-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1a482-119">存取類型：唯讀</span><span class="sxs-lookup"><span data-stu-id="1a482-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a482-120">主機一次可接受的工作階段數目上限。</span><span class="sxs-lookup"><span data-stu-id="1a482-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a482-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="1a482-121">Requirements</span></span>  
  
|<span data-ttu-id="1a482-122">MOF</span><span class="sxs-lookup"><span data-stu-id="1a482-122">MOF</span></span>|<span data-ttu-id="1a482-123">於 Servicemodel.mof 中宣告。</span><span class="sxs-lookup"><span data-stu-id="1a482-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1a482-124">命名空間</span><span class="sxs-lookup"><span data-stu-id="1a482-124">Namespace</span></span>|<span data-ttu-id="1a482-125">於 root\ServiceModel 中定義</span><span class="sxs-lookup"><span data-stu-id="1a482-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a482-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a482-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
