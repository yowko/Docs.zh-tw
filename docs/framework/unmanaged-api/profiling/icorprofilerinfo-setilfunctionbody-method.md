---
title: ICorProfilerInfo::SetILFunctionBody 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 296c3973403a5b09332efa24961d7a474d814aab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863344"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="5250d-102">ICorProfilerInfo::SetILFunctionBody 方法</span><span class="sxs-lookup"><span data-stu-id="5250d-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="5250d-103">取代指定模組中所指定函式的主體。</span><span class="sxs-lookup"><span data-stu-id="5250d-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5250d-104">語法</span><span class="sxs-lookup"><span data-stu-id="5250d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5250d-105">參數</span><span class="sxs-lookup"><span data-stu-id="5250d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="5250d-106">在函數所在模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5250d-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="5250d-107">在要取代主體之函式的 token。</span><span class="sxs-lookup"><span data-stu-id="5250d-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="5250d-108">在函數的新標頭。</span><span class="sxs-lookup"><span data-stu-id="5250d-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5250d-109">備註</span><span class="sxs-lookup"><span data-stu-id="5250d-109">Remarks</span></span>  
 <span data-ttu-id="5250d-110">`SetILFunctionBody` 方法會取代中繼資料中函數的相對虛擬位址，使其指向新的函式主體，並視需要調整任何內部資料結構。</span><span class="sxs-lookup"><span data-stu-id="5250d-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="5250d-111">只有從未由即時（JIT）編譯器編譯的函式，才能呼叫 `SetILFunctionBody` 方法。</span><span class="sxs-lookup"><span data-stu-id="5250d-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="5250d-112">使用[ICorProfilerInfo：： GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)方法來配置新方法的空間，以確保緩衝區相容。</span><span class="sxs-lookup"><span data-stu-id="5250d-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5250d-113">需求</span><span class="sxs-lookup"><span data-stu-id="5250d-113">Requirements</span></span>  
 <span data-ttu-id="5250d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5250d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5250d-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5250d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5250d-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5250d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5250d-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5250d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5250d-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="5250d-118">See also</span></span>

- [<span data-ttu-id="5250d-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5250d-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
