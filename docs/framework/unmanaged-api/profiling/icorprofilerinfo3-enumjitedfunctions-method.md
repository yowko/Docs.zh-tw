---
title: ICorProfilerInfo3::EnumJITedFunctions 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862421"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="11684-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="11684-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="11684-103">傳回先前已進行 JIT 編譯之所有函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="11684-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11684-104">語法</span><span class="sxs-lookup"><span data-stu-id="11684-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11684-105">參數</span><span class="sxs-lookup"><span data-stu-id="11684-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="11684-106">脫銷[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="11684-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11684-107">備註</span><span class="sxs-lookup"><span data-stu-id="11684-107">Remarks</span></span>  
 <span data-ttu-id="11684-108">這個方法可能會與 `JITCompilation` 回呼（例如[ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md)方法）重迭。</span><span class="sxs-lookup"><span data-stu-id="11684-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="11684-109">這個方法所傳回的列舉值不包含從 Ngen.exe 產生的原生映射載入的函式。</span><span class="sxs-lookup"><span data-stu-id="11684-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11684-110">針對 [`COR_PRF_FUNCTION::reJitId`] 欄位的值，傳回的列舉只包含 "0"。</span><span class="sxs-lookup"><span data-stu-id="11684-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="11684-111">如果您需要有效的 `COR_PRF_FUNCTION::reJitId` 值，請使用[ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="11684-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11684-112">需求</span><span class="sxs-lookup"><span data-stu-id="11684-112">Requirements</span></span>  
 <span data-ttu-id="11684-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11684-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11684-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11684-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11684-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11684-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11684-116">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11684-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11684-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="11684-117">See also</span></span>

- [<span data-ttu-id="11684-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="11684-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="11684-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="11684-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11684-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="11684-120">Profiling</span></span>](index.md)
