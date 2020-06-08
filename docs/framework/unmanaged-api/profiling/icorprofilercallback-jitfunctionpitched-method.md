---
title: ICorProfilerCallback::JITFunctionPitched 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500022"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="fa538-102">ICorProfilerCallback::JITFunctionPitched 方法</span><span class="sxs-lookup"><span data-stu-id="fa538-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="fa538-103">通知分析工具，已從記憶體中移除已經過時間（JIT）編譯的函式。</span><span class="sxs-lookup"><span data-stu-id="fa538-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa538-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa538-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa538-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa538-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fa538-106">在已移除之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fa538-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa538-107">備註</span><span class="sxs-lookup"><span data-stu-id="fa538-107">Remarks</span></span>  
 <span data-ttu-id="fa538-108">如果呼叫移除的函式，分析工具將會在重新編譯函數時接收新的 JIT 編譯事件。</span><span class="sxs-lookup"><span data-stu-id="fa538-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="fa538-109">目前，common language runtime （CLR） JIT 編譯程式不會從記憶體中移除函式，因此目前不會使用此回呼，而且分析工具將不會收到此回撥。</span><span class="sxs-lookup"><span data-stu-id="fa538-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="fa538-110">在重新編譯函數之前，的值無效 `functionId` 。</span><span class="sxs-lookup"><span data-stu-id="fa538-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="fa538-111">重新編譯函式時， `functionId` 將會使用相同的值。</span><span class="sxs-lookup"><span data-stu-id="fa538-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa538-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="fa538-112">Requirements</span></span>  
 <span data-ttu-id="fa538-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa538-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa538-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa538-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa538-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa538-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa538-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa538-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa538-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa538-117">See also</span></span>

- [<span data-ttu-id="fa538-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fa538-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
