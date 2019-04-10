---
title: ICorProfilerInfo5::SetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266219894ffefa0d4066c6ca68c7cadf6265e098
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175808"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="a1d08-102">ICorProfilerInfo5::SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="a1d08-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="a1d08-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="a1d08-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a1d08-104">設定值，以指定分析工具要從通用語言執行時期 (CLR) 接收事件通知之來源事件的類型。</span><span class="sxs-lookup"><span data-stu-id="a1d08-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="a1d08-105">它提供的功能多於[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a1d08-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1d08-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1d08-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1d08-107">參數</span><span class="sxs-lookup"><span data-stu-id="a1d08-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="a1d08-108">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="a1d08-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a1d08-109">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="a1d08-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a1d08-110">位元所述[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a1d08-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="a1d08-111">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="a1d08-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="a1d08-112">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="a1d08-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a1d08-113">位元所述[COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="a1d08-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1d08-114">備註</span><span class="sxs-lookup"><span data-stu-id="a1d08-114">Remarks</span></span>  
 <span data-ttu-id="a1d08-115">`SetEventMask2` 方法可用於設定分析工具所訂閱的回呼。</span><span class="sxs-lookup"><span data-stu-id="a1d08-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="a1d08-116">一般而言，您呼叫[GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)方法，以判斷哪一個位元已設定，執行的邏輯 OR 其`pdwEventsLow`並`pdwEventsHigh`值和您想要設定，然後再呼叫任何新位元`SetEventMask2`方法。</span><span class="sxs-lookup"><span data-stu-id="a1d08-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="a1d08-117">這個方法會以建議的替代做法[SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a1d08-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1d08-118">需求</span><span class="sxs-lookup"><span data-stu-id="a1d08-118">Requirements</span></span>  
 <span data-ttu-id="a1d08-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a1d08-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1d08-120">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1d08-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1d08-121">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1d08-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a1d08-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="a1d08-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1d08-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1d08-123">See also</span></span>

- [<span data-ttu-id="a1d08-124">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="a1d08-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="a1d08-125">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="a1d08-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
