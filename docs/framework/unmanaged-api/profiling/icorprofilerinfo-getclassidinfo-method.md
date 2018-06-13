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
ms.openlocfilehash: 193cbf3fe7ba99a70039c11983c6a203337290eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453681"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="62dd6-102">ICorProfilerInfo::GetClassIDInfo 方法</span><span class="sxs-lookup"><span data-stu-id="62dd6-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="62dd6-103">取得父模組和中繼資料語彙基元，為指定的類別。</span><span class="sxs-lookup"><span data-stu-id="62dd6-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62dd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="62dd6-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62dd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="62dd6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="62dd6-106">[in]要取得的資訊類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="62dd6-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="62dd6-107">[out]此類別父模組的識別碼指標。</span><span class="sxs-lookup"><span data-stu-id="62dd6-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="62dd6-108">[out]此類別中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="62dd6-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62dd6-109">備註</span><span class="sxs-lookup"><span data-stu-id="62dd6-109">Remarks</span></span>  
 <span data-ttu-id="62dd6-110">分析工具程式碼可以呼叫[icorprofilerinfo:: Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)來取得提供之模組的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="62dd6-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="62dd6-111">然後，傳回至 `pTypeDefToken` 所參考位置的中繼資料語彙基元可以用來存取此類別的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="62dd6-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="62dd6-112">若要取得泛型類型的詳細資訊，請使用[icorprofilerinfo2:: Getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62dd6-113">需求</span><span class="sxs-lookup"><span data-stu-id="62dd6-113">Requirements</span></span>  
 <span data-ttu-id="62dd6-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62dd6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62dd6-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62dd6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62dd6-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62dd6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62dd6-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62dd6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62dd6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62dd6-118">See Also</span></span>  
 [<span data-ttu-id="62dd6-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="62dd6-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
