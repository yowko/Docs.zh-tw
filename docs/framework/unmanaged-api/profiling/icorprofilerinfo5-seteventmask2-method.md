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
ms.openlocfilehash: 6cc1cfadd809b7406845596ace78e308ccbf529a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455993"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="fb301-102">ICorProfilerInfo5::SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="fb301-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="fb301-103">[在 .NET Framework 4.5.2 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="fb301-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fb301-104">設定值，以指定分析工具要從通用語言執行時期 (CLR) 接收事件通知之來源事件的類型。</span><span class="sxs-lookup"><span data-stu-id="fb301-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="fb301-105">它提供的功能多於[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fb301-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb301-106">語法</span><span class="sxs-lookup"><span data-stu-id="fb301-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb301-107">參數</span><span class="sxs-lookup"><span data-stu-id="fb301-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="fb301-108">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="fb301-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="fb301-109">每個位元分別控制不同的功能、行為或事件類型。</span><span class="sxs-lookup"><span data-stu-id="fb301-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="fb301-110">中所述的位元[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="fb301-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="fb301-111">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="fb301-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="fb301-112">每個位元分別控制不同的功能、行為或事件類型。</span><span class="sxs-lookup"><span data-stu-id="fb301-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="fb301-113">中所述的位元[COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="fb301-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb301-114">備註</span><span class="sxs-lookup"><span data-stu-id="fb301-114">Remarks</span></span>  
 <span data-ttu-id="fb301-115">`SetEventMask2` 方法可用於設定分析工具所訂閱的回呼。</span><span class="sxs-lookup"><span data-stu-id="fb301-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="fb301-116">通常您會呼叫[GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)方法，以判斷要設定，執行的邏輯 OR 其`pdwEventsLow`和`pdwEventsHigh`值和您想要設定，然後再呼叫任何新位元`SetEventMask2`方法。</span><span class="sxs-lookup"><span data-stu-id="fb301-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="fb301-117">這個方法會以建議的替代做法[SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="fb301-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb301-118">需求</span><span class="sxs-lookup"><span data-stu-id="fb301-118">Requirements</span></span>  
 <span data-ttu-id="fb301-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fb301-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb301-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fb301-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fb301-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fb301-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb301-122">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb301-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb301-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb301-123">See Also</span></span>  
 [<span data-ttu-id="fb301-124">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="fb301-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="fb301-125">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="fb301-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
