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
ms.openlocfilehash: 6227baaead518eae2de5913369b72de1072ac052
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681492"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="0fdeb-102">ICorProfilerInfo3::EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="0fdeb-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>

<span data-ttu-id="0fdeb-103">傳回先前 JIT 編譯之所有函式的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fdeb-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fdeb-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fdeb-105">參數</span><span class="sxs-lookup"><span data-stu-id="0fdeb-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="0fdeb-106">擴展 [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) 列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fdeb-107">備註</span><span class="sxs-lookup"><span data-stu-id="0fdeb-107">Remarks</span></span>  

 <span data-ttu-id="0fdeb-108">這個方法可能與 `JITCompilation` 回呼（例如 [ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) 方法）重迭。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="0fdeb-109">這個方法所傳回的列舉值不包含從使用 Ngen.exe 產生的原生映射載入的函式。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0fdeb-110">傳回的列舉只針對欄位的值包含 "0" `COR_PRF_FUNCTION::reJitId` 。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="0fdeb-111">如果您需要有效 `COR_PRF_FUNCTION::reJitId` 的值，請使用 [ICorProfilerInfo4：： EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fdeb-112">需求</span><span class="sxs-lookup"><span data-stu-id="0fdeb-112">Requirements</span></span>  

 <span data-ttu-id="0fdeb-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fdeb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fdeb-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0fdeb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0fdeb-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fdeb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fdeb-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fdeb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fdeb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fdeb-117">See also</span></span>

- [<span data-ttu-id="0fdeb-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="0fdeb-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0fdeb-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="0fdeb-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0fdeb-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="0fdeb-120">Profiling</span></span>](index.md)
