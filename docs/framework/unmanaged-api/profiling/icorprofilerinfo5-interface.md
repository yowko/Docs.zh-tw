---
title: "ICorProfilerInfo5 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 75bbaf5fdf41a55719965203c50ddd0f5d48263a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="d7dfb-102">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="d7dfb-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="d7dfb-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="d7dfb-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d7dfb-104">子類別[ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) ，提供程式碼分析工具用來通訊與 common language runtime (CLR)，以控制事件監視的方法。</span><span class="sxs-lookup"><span data-stu-id="d7dfb-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7dfb-105">方法</span><span class="sxs-lookup"><span data-stu-id="d7dfb-105">Methods</span></span>  
  
|<span data-ttu-id="d7dfb-106">方法</span><span class="sxs-lookup"><span data-stu-id="d7dfb-106">Method</span></span>|<span data-ttu-id="d7dfb-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7dfb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7dfb-108">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="d7dfb-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="d7dfb-109">取得分析工具想要從 CLR 接收的目前事件分類通知。</span><span class="sxs-lookup"><span data-stu-id="d7dfb-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="d7dfb-110">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="d7dfb-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="d7dfb-111">設定一個值，以指定分析工具想要從 CLR 接收事件通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="d7dfb-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7dfb-112">備註</span><span class="sxs-lookup"><span data-stu-id="d7dfb-112">Remarks</span></span>  
 <span data-ttu-id="d7dfb-113">此介面上的可用方法的目的是要取代[icorprofilerinfo:: Geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)和[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d7dfb-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7dfb-114">需求</span><span class="sxs-lookup"><span data-stu-id="d7dfb-114">Requirements</span></span>  
 <span data-ttu-id="d7dfb-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7dfb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7dfb-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7dfb-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7dfb-117">**.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7dfb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7dfb-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="d7dfb-118">See Also</span></span>  
 [<span data-ttu-id="d7dfb-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="d7dfb-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
