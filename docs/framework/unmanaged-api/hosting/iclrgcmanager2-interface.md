---
title: ICLRGCManager2 介面
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
ms.openlocfilehash: d2873b5e1f8229e8a16dfaacf1c9737ac47405bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672795"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="3001f-102">ICLRGCManager2 介面</span><span class="sxs-lookup"><span data-stu-id="3001f-102">ICLRGCManager2 Interface</span></span>

<span data-ttu-id="3001f-103">提供可讓主機與 common language runtime 的垃圾收集系統互動的方法。</span><span class="sxs-lookup"><span data-stu-id="3001f-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3001f-104">方法</span><span class="sxs-lookup"><span data-stu-id="3001f-104">Methods</span></span>  
  
|<span data-ttu-id="3001f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3001f-105">Method</span></span>|<span data-ttu-id="3001f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3001f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3001f-107">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="3001f-107">SetGCStartupLimitsEx Method</span></span>](iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="3001f-108">設定垃圾收集區段的大小，以及垃圾收集系統之層代0的大小上限。</span><span class="sxs-lookup"><span data-stu-id="3001f-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="3001f-109">啟用超出的層代0和區段大小 `DWORD` 。</span><span class="sxs-lookup"><span data-stu-id="3001f-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3001f-110">備註</span><span class="sxs-lookup"><span data-stu-id="3001f-110">Remarks</span></span>  

 <span data-ttu-id="3001f-111">此介面繼承自 [ICLRGCManager 介面](iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="3001f-111">This interface inherits from the [ICLRGCManager Interface](iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="3001f-112">Common language runtime (CLR) 以 managed 類型來實行其垃圾收集機制 <xref:System.GC> 。</span><span class="sxs-lookup"><span data-stu-id="3001f-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="3001f-113">如需垃圾收集系統的詳細資訊，請參閱 [垃圾收集](../../../standard/garbage-collection/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3001f-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3001f-114">需求</span><span class="sxs-lookup"><span data-stu-id="3001f-114">Requirements</span></span>  

 <span data-ttu-id="3001f-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3001f-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3001f-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3001f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3001f-117">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="3001f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3001f-118">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3001f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3001f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3001f-119">See also</span></span>

- [<span data-ttu-id="3001f-120">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="3001f-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="3001f-121">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="3001f-121">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="3001f-122">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="3001f-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3001f-123">.NET Framework 4 和 4.5 中新增的 CLR 裝載介面</span><span class="sxs-lookup"><span data-stu-id="3001f-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="3001f-124">裝載介面</span><span class="sxs-lookup"><span data-stu-id="3001f-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="3001f-125">裝載</span><span class="sxs-lookup"><span data-stu-id="3001f-125">Hosting</span></span>](index.md)
