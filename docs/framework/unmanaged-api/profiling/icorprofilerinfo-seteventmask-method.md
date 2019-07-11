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
ms.openlocfilehash: 6f3f61caf0f4993c49d2956a37068aa826c4ac29
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772121"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="f1fbe-102">ICorProfilerInfo::SetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="f1fbe-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="f1fbe-103">設定一個值，以指定分析工具想要從通用語言執行平台 (CLR) 接收其通知的事件類型。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1fbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1fbe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1fbe-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1fbe-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="f1fbe-106">[in] 4 個位元組的值，可指定事件的分類。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="f1fbe-107">每個位元各控制事件的不同功能、行為或類型。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="f1fbe-108">位元所述[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1fbe-109">備註</span><span class="sxs-lookup"><span data-stu-id="f1fbe-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1fbe-110">您應該呼叫[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)而不是這個方法的方法。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="f1fbe-111">雖然`SetEventMask`方法會繼續受到支援， [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)提供額外的功能。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1fbe-112">需求</span><span class="sxs-lookup"><span data-stu-id="f1fbe-112">Requirements</span></span>  
 <span data-ttu-id="f1fbe-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1fbe-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1fbe-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f1fbe-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1fbe-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1fbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1fbe-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1fbe-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fbe-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1fbe-117">See also</span></span>

- [<span data-ttu-id="f1fbe-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f1fbe-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f1fbe-119">SetEventMask2 方法</span><span class="sxs-lookup"><span data-stu-id="f1fbe-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
