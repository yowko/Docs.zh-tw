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
ms.openlocfilehash: 91483d5bdf1eb8e6b03d7691e2a95074e3789317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134872"
---
# <a name="igchost-interface"></a><span data-ttu-id="f6174-102">IGCHost 介面</span><span class="sxs-lookup"><span data-stu-id="f6174-102">IGCHost Interface</span></span>
<span data-ttu-id="f6174-103">提供方法來取得垃圾收集系統的相關資訊，以及控制垃圾收集的某些層面。</span><span class="sxs-lookup"><span data-stu-id="f6174-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6174-104">從 .NET Framework 4.5 開始，您可以使用[IGCHost2：： SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)方法，將垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限設定為大於 `DWORD` 限制的值這是由[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)方法所加諸的。</span><span class="sxs-lookup"><span data-stu-id="f6174-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6174-105">此介面僅供專家使用。</span><span class="sxs-lookup"><span data-stu-id="f6174-105">This interface is for expert usage only.</span></span> <span data-ttu-id="f6174-106">如果未正確使用，它可能會影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="f6174-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6174-107">方法</span><span class="sxs-lookup"><span data-stu-id="f6174-107">Methods</span></span>  
  
|<span data-ttu-id="f6174-108">方法</span><span class="sxs-lookup"><span data-stu-id="f6174-108">Method</span></span>|<span data-ttu-id="f6174-109">描述</span><span class="sxs-lookup"><span data-stu-id="f6174-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6174-110">Collect 方法</span><span class="sxs-lookup"><span data-stu-id="f6174-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="f6174-111">無論目前垃圾收集的狀態為何，都會強制針對給定的層代進行集合。</span><span class="sxs-lookup"><span data-stu-id="f6174-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="f6174-112">GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="f6174-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="f6174-113">取得垃圾收集系統目前狀態的統計資料。</span><span class="sxs-lookup"><span data-stu-id="f6174-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="f6174-114">GetThreadStats 方法</span><span class="sxs-lookup"><span data-stu-id="f6174-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="f6174-115">取得垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="f6174-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="f6174-116">SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="f6174-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="f6174-117">設定層代0的區段大小和大小上限。</span><span class="sxs-lookup"><span data-stu-id="f6174-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="f6174-118">SetVirtualMemLimit 方法</span><span class="sxs-lookup"><span data-stu-id="f6174-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="f6174-119">設定執行時間虛擬記憶體的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f6174-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f6174-120">需求</span><span class="sxs-lookup"><span data-stu-id="f6174-120">Requirements</span></span>  
 <span data-ttu-id="f6174-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6174-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6174-122">**標頭：** GCHost .idl，GCHost。h</span><span class="sxs-lookup"><span data-stu-id="f6174-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f6174-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f6174-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6174-124">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6174-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6174-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6174-125">See also</span></span>

- [<span data-ttu-id="f6174-126">裝載介面</span><span class="sxs-lookup"><span data-stu-id="f6174-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f6174-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="f6174-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
