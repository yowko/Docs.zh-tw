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
ms.openlocfilehash: 5272c5bf256f6e21a83470db094ab79317932018
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497474"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="83d80-102">ICorProfilerInfo::SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="83d80-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="83d80-103">指定將被呼叫來對應 `FunctionID` 值到替代值的程式碼剖析工具實作函式，這會被傳遞至分析工具函式進入/離開的攔截。</span><span class="sxs-lookup"><span data-stu-id="83d80-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83d80-104">語法</span><span class="sxs-lookup"><span data-stu-id="83d80-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83d80-105">參數</span><span class="sxs-lookup"><span data-stu-id="83d80-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="83d80-106">在將呼叫以將[FunctionIDMapper](functionidmapper-function.md) `FunctionID` 值對應至其替代值的 FunctionIDMapper 執行的指標。</span><span class="sxs-lookup"><span data-stu-id="83d80-106">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83d80-107">備註</span><span class="sxs-lookup"><span data-stu-id="83d80-107">Remarks</span></span>  
 <span data-ttu-id="83d80-108">值的替代專案 `FunctionID` 會傳遞給分析工具的函式進入/結束攔截器（[FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和[FunctionTailcall2](functiontailcall2-function.md)），這些是由[ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)方法所指定。</span><span class="sxs-lookup"><span data-stu-id="83d80-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="83d80-109">只能 `FunctionIDMapper` 設定一次，建議您在[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)回呼中設定它。</span><span class="sxs-lookup"><span data-stu-id="83d80-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83d80-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="83d80-110">Requirements</span></span>  
 <span data-ttu-id="83d80-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83d80-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83d80-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83d80-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83d80-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83d80-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83d80-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83d80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83d80-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83d80-115">See also</span></span>

- [<span data-ttu-id="83d80-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="83d80-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
