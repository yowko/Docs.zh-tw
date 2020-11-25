---
title: ICorProfilerCallback::Initialize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: 26df1599af247bd08d3702d4ef3c5aa2f648620c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720369"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="f3772-102">ICorProfilerCallback::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="f3772-102">ICorProfilerCallback::Initialize Method</span></span>

<span data-ttu-id="f3772-103">每當新的 common language runtime (CLR) 應用程式啟動時呼叫，就會將程式碼分析工具初始化。</span><span class="sxs-lookup"><span data-stu-id="f3772-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3772-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3772-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3772-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3772-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="f3772-106">\[in] 程式碼剖析工具必須查詢[ICorProfilerInfo](icorprofilerinfo-interface.md)介面指標的[IUnknown](/cpp/atl/iunknown)介面指標。</span><span class="sxs-lookup"><span data-stu-id="f3772-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f3772-107">備註</span><span class="sxs-lookup"><span data-stu-id="f3772-107">Remarks</span></span>  

 <span data-ttu-id="f3772-108">`Initialize`呼叫是啟用 (或停用不可變) 回呼的唯一機會。</span><span class="sxs-lookup"><span data-stu-id="f3772-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="f3772-109">一旦呼叫啟用回呼 `Initialize` ，之後就無法使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)停用回呼。</span><span class="sxs-lookup"><span data-stu-id="f3772-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="f3772-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值指出哪些事件是不可變的。</span><span class="sxs-lookup"><span data-stu-id="f3772-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3772-111">需求</span><span class="sxs-lookup"><span data-stu-id="f3772-111">Requirements</span></span>  

 <span data-ttu-id="f3772-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3772-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3772-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3772-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3772-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3772-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3772-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3772-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3772-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3772-116">See also</span></span>

- [<span data-ttu-id="f3772-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f3772-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f3772-118">Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="f3772-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
