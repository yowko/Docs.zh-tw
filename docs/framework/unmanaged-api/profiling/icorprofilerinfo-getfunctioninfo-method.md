---
title: ICorProfilerInfo::GetFunctionInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863617"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="db9ee-102">ICorProfilerInfo::GetFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="db9ee-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="db9ee-103">取得所指定函式的父類別和元資料標記。</span><span class="sxs-lookup"><span data-stu-id="db9ee-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db9ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="db9ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db9ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="db9ee-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="db9ee-106">在要取得其父類別和元資料標記的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="db9ee-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="db9ee-107">[out] 函式父類別的指標。</span><span class="sxs-lookup"><span data-stu-id="db9ee-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="db9ee-108">[out] 定義函式父類別的模組指標。</span><span class="sxs-lookup"><span data-stu-id="db9ee-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="db9ee-109">[out] 此函式中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="db9ee-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db9ee-110">備註</span><span class="sxs-lookup"><span data-stu-id="db9ee-110">Remarks</span></span>  
 <span data-ttu-id="db9ee-111">分析工具程式碼可以呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)來取得給定模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="db9ee-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="db9ee-112">然後，傳回至 `pToken` 所參考位置的中繼資料語彙基元可以用來存取此函式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="db9ee-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="db9ee-113">如需使用函式的詳細資訊，可能無法在泛型類別上取得函數的 `ClassID`。</span><span class="sxs-lookup"><span data-stu-id="db9ee-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="db9ee-114">在此情況下，`pClassId` 將會是0。</span><span class="sxs-lookup"><span data-stu-id="db9ee-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="db9ee-115">Profiler 程式碼應該使用[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)搭配 COR_PRF_FRAME_INFO 值，以提供更多內容。</span><span class="sxs-lookup"><span data-stu-id="db9ee-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db9ee-116">需求</span><span class="sxs-lookup"><span data-stu-id="db9ee-116">Requirements</span></span>  
 <span data-ttu-id="db9ee-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db9ee-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db9ee-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="db9ee-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db9ee-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db9ee-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db9ee-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db9ee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9ee-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="db9ee-121">See also</span></span>

- [<span data-ttu-id="db9ee-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="db9ee-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
