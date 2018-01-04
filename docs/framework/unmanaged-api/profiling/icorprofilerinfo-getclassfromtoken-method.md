---
title: "ICorProfilerInfo::GetClassFromToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassFromToken
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9972a9d97f94a6286adc0906416349f92e6bf7ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="a26e0-102">ICorProfilerInfo::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="a26e0-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="a26e0-103">取得指定中繼資料語彙基元的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="a26e0-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="a26e0-104">這個方法是.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="a26e0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a26e0-105">使用[icorprofilerinfo2:: Getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)改為。</span><span class="sxs-lookup"><span data-stu-id="a26e0-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26e0-106">語法</span><span class="sxs-lookup"><span data-stu-id="a26e0-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a26e0-107">參數</span><span class="sxs-lookup"><span data-stu-id="a26e0-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="a26e0-108">[in]包含類別之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a26e0-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="a26e0-109">[in]`mdTypeDef`參考類別的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a26e0-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="a26e0-110">[out]指向的類別識別碼。</span><span class="sxs-lookup"><span data-stu-id="a26e0-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a26e0-111">備註</span><span class="sxs-lookup"><span data-stu-id="a26e0-111">Remarks</span></span>  
 <span data-ttu-id="a26e0-112">這個方法已過時。請改用`ICorProfilerInfo2::GetClassFromTokenAndTypeArgs`所有類型。</span><span class="sxs-lookup"><span data-stu-id="a26e0-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26e0-113">需求</span><span class="sxs-lookup"><span data-stu-id="a26e0-113">Requirements</span></span>  
 <span data-ttu-id="a26e0-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a26e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26e0-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a26e0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a26e0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a26e0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a26e0-117">**.NET framework 版本：** 1.0、 1.1</span><span class="sxs-lookup"><span data-stu-id="a26e0-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26e0-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="a26e0-118">See Also</span></span>  
 [<span data-ttu-id="a26e0-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="a26e0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
