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
ms.openlocfilehash: 12b4b897f9dc51175037d39c0368b6ce59fefefb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498475"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="76f5c-102">ICorProfilerInfo::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="76f5c-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="76f5c-103">取得指定元資料標記之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76f5c-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="76f5c-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="76f5c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="76f5c-105">請改用[ICorProfilerInfo2：： GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="76f5c-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f5c-106">語法</span><span class="sxs-lookup"><span data-stu-id="76f5c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f5c-107">參數</span><span class="sxs-lookup"><span data-stu-id="76f5c-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="76f5c-108">在包含類別之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="76f5c-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="76f5c-109">在`mdTypeDef`參考類別的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="76f5c-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="76f5c-110">脫銷類別識別碼的指標。</span><span class="sxs-lookup"><span data-stu-id="76f5c-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76f5c-111">備註</span><span class="sxs-lookup"><span data-stu-id="76f5c-111">Remarks</span></span>  
 <span data-ttu-id="76f5c-112">這個方法已過時;請改用 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` 適用于所有類型的。</span><span class="sxs-lookup"><span data-stu-id="76f5c-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f5c-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="76f5c-113">Requirements</span></span>  
 <span data-ttu-id="76f5c-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76f5c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f5c-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76f5c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76f5c-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76f5c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f5c-117">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="76f5c-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f5c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76f5c-118">See also</span></span>

- [<span data-ttu-id="76f5c-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="76f5c-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
