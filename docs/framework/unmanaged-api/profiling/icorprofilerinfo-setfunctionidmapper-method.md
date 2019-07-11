---
title: ICorProfilerInfo::SetFunctionIDMapper 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4eefbb100b215cf4ac98352f37488b21cde49d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772145"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="c4bcc-102">ICorProfilerInfo::SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="c4bcc-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="c4bcc-103">指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。</span><span class="sxs-lookup"><span data-stu-id="c4bcc-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4bcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4bcc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4bcc-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4bcc-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="c4bcc-106">[in]指標[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)將會呼叫對應的實作`FunctionID`其替代值的值。</span><span class="sxs-lookup"><span data-stu-id="c4bcc-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4bcc-107">備註</span><span class="sxs-lookup"><span data-stu-id="c4bcc-107">Remarks</span></span>  
 <span data-ttu-id="c4bcc-108">替代方式`FunctionID`值會傳遞至分析工具的函式進入/離開的攔截 ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md))所指定之[ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c4bcc-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="c4bcc-109">`FunctionIDMapper` Lze nastavit pouze jednou，建議您將它設定[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="c4bcc-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4bcc-110">需求</span><span class="sxs-lookup"><span data-stu-id="c4bcc-110">Requirements</span></span>  
 <span data-ttu-id="c4bcc-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4bcc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4bcc-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c4bcc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4bcc-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4bcc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4bcc-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4bcc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4bcc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4bcc-115">See also</span></span>

- [<span data-ttu-id="c4bcc-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="c4bcc-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
