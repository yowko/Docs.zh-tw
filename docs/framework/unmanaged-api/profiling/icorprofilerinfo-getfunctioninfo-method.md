---
title: "ICorProfilerInfo::GetFunctionInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17512077ef7a8ca45fa76c00f93612015948d083
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="f24f9-102">ICorProfilerInfo::GetFunctionInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f24f9-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="f24f9-103">取得父類別和中繼資料語彙基元的指定函式。</span><span class="sxs-lookup"><span data-stu-id="f24f9-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f24f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="f24f9-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f24f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="f24f9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f24f9-106">[in]要取得的父類別和中繼資料語彙基元函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f24f9-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="f24f9-107">[out] 函式父類別的指標。</span><span class="sxs-lookup"><span data-stu-id="f24f9-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f24f9-108">[out] 定義函式父類別的模組指標。</span><span class="sxs-lookup"><span data-stu-id="f24f9-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="f24f9-109">[out] 此函式中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="f24f9-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f24f9-110">備註</span><span class="sxs-lookup"><span data-stu-id="f24f9-110">Remarks</span></span>  
 <span data-ttu-id="f24f9-111">分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)來取得提供之模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="f24f9-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="f24f9-112">然後，傳回至 `pToken` 所參考位置的中繼資料語彙基元可以用來存取此函式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="f24f9-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="f24f9-113">`ClassID`泛型類別上的函式可能需要多個內容使用的相關資訊的函式。</span><span class="sxs-lookup"><span data-stu-id="f24f9-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="f24f9-114">在此情況下，`pClassId`將會是 0。</span><span class="sxs-lookup"><span data-stu-id="f24f9-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="f24f9-115">分析工具程式碼應該使用[icorprofilerinfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) COR_PRF_FRAME_INFO 值來提供更多的內容。</span><span class="sxs-lookup"><span data-stu-id="f24f9-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f24f9-116">需求</span><span class="sxs-lookup"><span data-stu-id="f24f9-116">Requirements</span></span>  
 <span data-ttu-id="f24f9-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f24f9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f24f9-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f24f9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f24f9-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f24f9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f24f9-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f24f9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f24f9-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f24f9-121">See Also</span></span>  
 [<span data-ttu-id="f24f9-122">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f24f9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
