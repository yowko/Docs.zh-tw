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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00b20134c0134aa30d2056b634c8525f66ed8cf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602452"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="b9d2d-102">ICorProfilerInfo::GetFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="b9d2d-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="b9d2d-103">取得父類別和中繼資料語彙基元指定的函式。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9d2d-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b9d2d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9d2d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b9d2d-106">[in]要取得的父類別和中繼資料語彙基元函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b9d2d-107">[out] 函式父類別的指標。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b9d2d-108">[out] 定義函式父類別的模組指標。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="b9d2d-109">[out] 此函式中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d2d-110">備註</span><span class="sxs-lookup"><span data-stu-id="b9d2d-110">Remarks</span></span>  
 <span data-ttu-id="b9d2d-111">分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)來取得提供之模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="b9d2d-112">然後，傳回至 `pToken` 所參考位置的中繼資料語彙基元可以用來存取此函式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="b9d2d-113">`ClassID`泛型類別上的函式可能無法取得，而不需要更多的內容資訊使用的函式。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="b9d2d-114">在此情況下，`pClassId`將會是 0。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="b9d2d-115">Profiler 的程式碼應該使用[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) COR_PRF_FRAME_INFO 值，以提供更多的內容。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d2d-116">需求</span><span class="sxs-lookup"><span data-stu-id="b9d2d-116">Requirements</span></span>  
 <span data-ttu-id="b9d2d-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d2d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d2d-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b9d2d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9d2d-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9d2d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9d2d-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9d2d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d2d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d2d-121">See also</span></span>
- [<span data-ttu-id="b9d2d-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b9d2d-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
