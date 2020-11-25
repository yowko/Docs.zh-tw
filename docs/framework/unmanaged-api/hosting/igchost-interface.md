---
title: IGCHost 介面
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 8965797321e68443c01d05f97d147f2320a76739
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724290"
---
# <a name="igchost-interface"></a><span data-ttu-id="1943e-102">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="1943e-102">IGCHost Interface</span></span>

<span data-ttu-id="1943e-103">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="1943e-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1943e-104">從 .NET Framework 4.5 開始，您可以使用 [IGCHost2：： SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) 方法，將垃圾收集系統之層代0的大小設定為大於 `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) 方法所加諸之限制的值。</span><span class="sxs-lookup"><span data-stu-id="1943e-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1943e-105">這個介面僅供專家使用。</span><span class="sxs-lookup"><span data-stu-id="1943e-105">This interface is for expert usage only.</span></span> <span data-ttu-id="1943e-106">如果使用不當，可能會影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="1943e-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1943e-107">方法</span><span class="sxs-lookup"><span data-stu-id="1943e-107">Methods</span></span>  
  
|<span data-ttu-id="1943e-108">方法</span><span class="sxs-lookup"><span data-stu-id="1943e-108">Method</span></span>|<span data-ttu-id="1943e-109">描述</span><span class="sxs-lookup"><span data-stu-id="1943e-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1943e-110">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="1943e-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="1943e-111">無論目前垃圾收集的狀態為何，都會強制執行給定層代的集合。</span><span class="sxs-lookup"><span data-stu-id="1943e-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="1943e-112">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="1943e-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="1943e-113">取得垃圾收集系統目前狀態的統計資料。</span><span class="sxs-lookup"><span data-stu-id="1943e-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="1943e-114">GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="1943e-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="1943e-115">取得垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="1943e-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="1943e-116">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="1943e-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="1943e-117">設定層代0的區段大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="1943e-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="1943e-118">SetVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="1943e-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="1943e-119">設定執行時間的虛擬記憶體大小上限。</span><span class="sxs-lookup"><span data-stu-id="1943e-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1943e-120">需求</span><span class="sxs-lookup"><span data-stu-id="1943e-120">Requirements</span></span>  

 <span data-ttu-id="1943e-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1943e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1943e-122">**標頭：** GCHost .idl、GCHost。h</span><span class="sxs-lookup"><span data-stu-id="1943e-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1943e-123">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="1943e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1943e-124">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1943e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1943e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1943e-125">See also</span></span>

- [<span data-ttu-id="1943e-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1943e-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="1943e-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="1943e-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
