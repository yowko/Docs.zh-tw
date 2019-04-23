---
title: ICorProfilerInfo::GetClassIDInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45abb39fa7266e19bbd375b476f2ab48bfc5914d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129996"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="036df-102">ICorProfilerInfo::GetClassIDInfo 方法</span><span class="sxs-lookup"><span data-stu-id="036df-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="036df-103">取得指定的類別父模組和中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="036df-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="036df-104">語法</span><span class="sxs-lookup"><span data-stu-id="036df-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="036df-105">參數</span><span class="sxs-lookup"><span data-stu-id="036df-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="036df-106">[in]要取得的資訊類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="036df-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="036df-107">[out]此類別父模組的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="036df-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="036df-108">[out]此類別的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="036df-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="036df-109">備註</span><span class="sxs-lookup"><span data-stu-id="036df-109">Remarks</span></span>  
 <span data-ttu-id="036df-110">分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)來取得提供之模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="036df-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="036df-111">然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="036df-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="036df-112">若要取得為泛型類型的詳細資訊，請使用[ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)。</span><span class="sxs-lookup"><span data-stu-id="036df-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="036df-113">需求</span><span class="sxs-lookup"><span data-stu-id="036df-113">Requirements</span></span>  
 <span data-ttu-id="036df-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="036df-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="036df-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="036df-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="036df-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="036df-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="036df-117">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="036df-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="036df-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="036df-118">See also</span></span>

- [<span data-ttu-id="036df-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="036df-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
