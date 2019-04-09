---
title: ICorProfilerInfo5 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094251"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="16bb8-102">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="16bb8-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="16bb8-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="16bb8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="16bb8-104">子類別[ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)可用於程式碼分析工具 common language runtime (CLR)，以控制事件監視與通訊的方法。</span><span class="sxs-lookup"><span data-stu-id="16bb8-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="16bb8-105">方法</span><span class="sxs-lookup"><span data-stu-id="16bb8-105">Methods</span></span>  
  
|<span data-ttu-id="16bb8-106">方法</span><span class="sxs-lookup"><span data-stu-id="16bb8-106">Method</span></span>|<span data-ttu-id="16bb8-107">描述</span><span class="sxs-lookup"><span data-stu-id="16bb8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="16bb8-108">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="16bb8-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="16bb8-109">取得分析工具想要從 CLR 接收的目前事件分類通知。</span><span class="sxs-lookup"><span data-stu-id="16bb8-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="16bb8-110">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="16bb8-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="16bb8-111">設定一個值，以指定分析工具想要從 CLR 接收事件通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="16bb8-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16bb8-112">備註</span><span class="sxs-lookup"><span data-stu-id="16bb8-112">Remarks</span></span>  
 <span data-ttu-id="16bb8-113">此介面上的可用方法的目的是要取代[icorprofilerinfo:: Geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)並[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="16bb8-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16bb8-114">需求</span><span class="sxs-lookup"><span data-stu-id="16bb8-114">Requirements</span></span>  
 <span data-ttu-id="16bb8-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16bb8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16bb8-116">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16bb8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="16bb8-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="16bb8-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="16bb8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16bb8-118">See also</span></span>

- [<span data-ttu-id="16bb8-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="16bb8-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
