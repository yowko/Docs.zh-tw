---
title: ICorProfilerInfo::GetClassFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 580c554c968819ba4ef2ba52edeb5e754d33ac1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185262"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="d401d-102">ICorProfilerInfo::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="d401d-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="d401d-103">指定中繼資料語彙基元的情況下取得類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d401d-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="d401d-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="d401d-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d401d-105">使用[ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="d401d-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d401d-106">語法</span><span class="sxs-lookup"><span data-stu-id="d401d-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d401d-107">參數</span><span class="sxs-lookup"><span data-stu-id="d401d-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d401d-108">[in]包含類別的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="d401d-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="d401d-109">[in]`mdTypeDef`參考類別的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d401d-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="d401d-110">[out]變數的指標，該類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="d401d-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d401d-111">備註</span><span class="sxs-lookup"><span data-stu-id="d401d-111">Remarks</span></span>  
 <span data-ttu-id="d401d-112">這個方法已經過時;請改用`ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`所有類型。</span><span class="sxs-lookup"><span data-stu-id="d401d-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d401d-113">需求</span><span class="sxs-lookup"><span data-stu-id="d401d-113">Requirements</span></span>  
 <span data-ttu-id="d401d-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d401d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d401d-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d401d-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d401d-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d401d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d401d-117">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d401d-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d401d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d401d-118">See also</span></span>

- [<span data-ttu-id="d401d-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d401d-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
