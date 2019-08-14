---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973868"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="0070c-102">ICorProfilerInfo8:: IsFunctionDynamic 方法</span><span class="sxs-lookup"><span data-stu-id="0070c-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>
  
  <span data-ttu-id="0070c-103">判斷函數是否沒有相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0070c-103">Determines if a function does not have associated metadata.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="0070c-104">語法</span><span class="sxs-lookup"><span data-stu-id="0070c-104">Syntax</span></span>  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a><span data-ttu-id="0070c-105">參數</span><span class="sxs-lookup"><span data-stu-id="0070c-105">Parameters</span></span>  
 `functionId` \
  <span data-ttu-id="0070c-106">在 `FunctionID`識別有問題之函數的。</span><span class="sxs-lookup"><span data-stu-id="0070c-106">[in]  The `FunctionID` that identifies the function in question.</span></span>

  `isDynamic` \
  <span data-ttu-id="0070c-107">脫銷的指標`BOOL` , 其中會包含一個值, 指出函式是否沒有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="0070c-107">[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="0070c-108">備註</span><span class="sxs-lookup"><span data-stu-id="0070c-108">Remarks</span></span>  
 <span data-ttu-id="0070c-109">如果函式沒有中繼資料, 則會將其視為動態。</span><span class="sxs-lookup"><span data-stu-id="0070c-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="0070c-110">某些方法 (例如 IL Stub 或 LCG 方法) 沒有相關聯的中繼資料可使用 IMetaDataImport Api 來抓取。</span><span class="sxs-lookup"><span data-stu-id="0070c-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="0070c-111">分析工具可以透過指令指標或接聽[ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md), 來發現這些方法。</span><span class="sxs-lookup"><span data-stu-id="0070c-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0070c-112">需求</span><span class="sxs-lookup"><span data-stu-id="0070c-112">Requirements</span></span>  
 <span data-ttu-id="0070c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0070c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0070c-114">**標頭：** Corprof.idl .idl, Corprof.idl。h</span><span class="sxs-lookup"><span data-stu-id="0070c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0070c-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0070c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0070c-116">**.NET Framework 版本:** [!包含[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="0070c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0070c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0070c-117">See also</span></span>
- [<span data-ttu-id="0070c-118">ICorProfilerInfo8 介面</span><span class="sxs-lookup"><span data-stu-id="0070c-118">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

