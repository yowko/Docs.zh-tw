---
title: ICorProfilerInfo::SetEventMask 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e11628f9c20160899f37e62472547eaa98ea60b8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962656"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="becf0-102">ICorProfilerInfo::SetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="becf0-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="becf0-103">設定一個值，以指定分析工具想要從通用語言執行平台 (CLR) 接收其通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="becf0-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="becf0-104">語法</span><span class="sxs-lookup"><span data-stu-id="becf0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="becf0-105">參數</span><span class="sxs-lookup"><span data-stu-id="becf0-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="becf0-106">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="becf0-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="becf0-107">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="becf0-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="becf0-108">[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉中會說明此位。</span><span class="sxs-lookup"><span data-stu-id="becf0-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="becf0-109">備註</span><span class="sxs-lookup"><span data-stu-id="becf0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="becf0-110">您應該呼叫[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法, 而不是這個方法。</span><span class="sxs-lookup"><span data-stu-id="becf0-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="becf0-111">雖然此`SetEventMask`方法會繼續受到支援, 但[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)會提供額外的功能。</span><span class="sxs-lookup"><span data-stu-id="becf0-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="becf0-112">需求</span><span class="sxs-lookup"><span data-stu-id="becf0-112">Requirements</span></span>  
 <span data-ttu-id="becf0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="becf0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="becf0-114">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="becf0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="becf0-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="becf0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="becf0-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="becf0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="becf0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="becf0-117">See also</span></span>

- [<span data-ttu-id="becf0-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="becf0-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="becf0-119">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="becf0-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
