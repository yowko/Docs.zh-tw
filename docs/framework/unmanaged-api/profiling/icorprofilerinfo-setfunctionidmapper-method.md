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
ms.openlocfilehash: 52ab9a089b5def4f3db2f99abc5a718d66cca739
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863448"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="ec5d0-102">ICorProfilerInfo::SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="ec5d0-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="ec5d0-103">指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。</span><span class="sxs-lookup"><span data-stu-id="ec5d0-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec5d0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec5d0-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec5d0-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="ec5d0-106">在將呼叫以將 `FunctionID` 值對應至其替代值的[FunctionIDMapper](functionidmapper-function.md)執行的指標。</span><span class="sxs-lookup"><span data-stu-id="ec5d0-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec5d0-107">備註</span><span class="sxs-lookup"><span data-stu-id="ec5d0-107">Remarks</span></span>  
 <span data-ttu-id="ec5d0-108">`FunctionID` 值的替代專案會傳遞至分析工具的函式進入/結束攔截器（[FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和[FunctionTailcall2](functiontailcall2-function.md)），這是由[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)方法所指定。</span><span class="sxs-lookup"><span data-stu-id="ec5d0-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="ec5d0-109">`FunctionIDMapper` 只能設定一次，建議您在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼中加以設定。</span><span class="sxs-lookup"><span data-stu-id="ec5d0-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec5d0-110">需求</span><span class="sxs-lookup"><span data-stu-id="ec5d0-110">Requirements</span></span>  
 <span data-ttu-id="ec5d0-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec5d0-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec5d0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec5d0-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec5d0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec5d0-114">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec5d0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5d0-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec5d0-115">See also</span></span>

- [<span data-ttu-id="ec5d0-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ec5d0-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
