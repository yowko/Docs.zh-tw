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
ms.openlocfilehash: 10e84b729c8af607165009a8591a69dbc1afcb1e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868378"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="407f3-102">ICorProfilerInfo5::SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="407f3-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="407f3-103">[.NET Framework 4.5.2 與更新版本提供支援]</span><span class="sxs-lookup"><span data-stu-id="407f3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="407f3-104">設定值，以指定分析工具要從通用語言執行時期 (CLR) 接收事件通知之來源事件的類型。</span><span class="sxs-lookup"><span data-stu-id="407f3-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="407f3-105">它提供的功能比[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法更多。</span><span class="sxs-lookup"><span data-stu-id="407f3-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407f3-106">語法</span><span class="sxs-lookup"><span data-stu-id="407f3-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="407f3-107">參數</span><span class="sxs-lookup"><span data-stu-id="407f3-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="407f3-108">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="407f3-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="407f3-109">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="407f3-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="407f3-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉中會描述位。</span><span class="sxs-lookup"><span data-stu-id="407f3-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="407f3-111">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="407f3-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="407f3-112">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="407f3-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="407f3-113">[COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md)列舉中會描述位。</span><span class="sxs-lookup"><span data-stu-id="407f3-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="407f3-114">備註</span><span class="sxs-lookup"><span data-stu-id="407f3-114">Remarks</span></span>  
 <span data-ttu-id="407f3-115">`SetEventMask2` 方法可用於設定分析工具所訂閱的回呼。</span><span class="sxs-lookup"><span data-stu-id="407f3-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="407f3-116">一般來說，您會呼叫[GetEventMask2](icorprofilerinfo5-geteventmask2-method.md)方法來判斷已設定的位、執行其 `pdwEventsLow` 的邏輯 OR，以及 `pdwEventsHigh` 值和任何您想要設定的新位，然後再呼叫 `SetEventMask2` 方法。</span><span class="sxs-lookup"><span data-stu-id="407f3-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="407f3-117">這是[SetEventMask](icorprofilerinfo-seteventmask-method.md)方法的建議替代方法。</span><span class="sxs-lookup"><span data-stu-id="407f3-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="407f3-118">需求</span><span class="sxs-lookup"><span data-stu-id="407f3-118">Requirements</span></span>  
 <span data-ttu-id="407f3-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="407f3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="407f3-120">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="407f3-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="407f3-121">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="407f3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="407f3-122">**.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="407f3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407f3-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="407f3-123">See also</span></span>

- [<span data-ttu-id="407f3-124">ICorProfilerInfo5 介面</span><span class="sxs-lookup"><span data-stu-id="407f3-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="407f3-125">GetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="407f3-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
