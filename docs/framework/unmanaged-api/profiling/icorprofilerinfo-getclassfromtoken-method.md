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
ms.openlocfilehash: 335c25316b34f79b8d02eea5a7dd4ed7994fc754
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780170"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="82048-102">ICorProfilerInfo::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="82048-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="82048-103">指定中繼資料語彙基元的情況下取得類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="82048-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="82048-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="82048-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="82048-105">使用[ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)改。</span><span class="sxs-lookup"><span data-stu-id="82048-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82048-106">語法</span><span class="sxs-lookup"><span data-stu-id="82048-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82048-107">參數</span><span class="sxs-lookup"><span data-stu-id="82048-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="82048-108">[in]包含類別的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="82048-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="82048-109">[in]`mdTypeDef`參考類別的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="82048-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="82048-110">[out]變數的指標，該類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="82048-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82048-111">備註</span><span class="sxs-lookup"><span data-stu-id="82048-111">Remarks</span></span>  
 <span data-ttu-id="82048-112">這個方法已經過時;請改用`ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`所有類型。</span><span class="sxs-lookup"><span data-stu-id="82048-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82048-113">需求</span><span class="sxs-lookup"><span data-stu-id="82048-113">Requirements</span></span>  
 <span data-ttu-id="82048-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82048-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82048-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82048-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82048-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82048-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82048-117">**.NET framework 版本：** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="82048-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82048-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82048-118">See also</span></span>

- [<span data-ttu-id="82048-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="82048-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
