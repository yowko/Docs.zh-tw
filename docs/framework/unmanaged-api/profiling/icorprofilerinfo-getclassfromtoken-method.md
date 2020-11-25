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
ms.openlocfilehash: 7d9fe7d6d5c5af32be22ba19b52e7d40033a6eb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706745"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="4fcf0-102">ICorProfilerInfo::GetClassFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="4fcf0-102">ICorProfilerInfo::GetClassFromToken Method</span></span>

<span data-ttu-id="4fcf0-103">取得類別的識別碼，指定元資料標記。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="4fcf0-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="4fcf0-105">請改用 [ICorProfilerInfo2：： GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fcf0-106">語法</span><span class="sxs-lookup"><span data-stu-id="4fcf0-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fcf0-107">參數</span><span class="sxs-lookup"><span data-stu-id="4fcf0-107">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="4fcf0-108">在包含類別之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="4fcf0-109">在 `mdTypeDef` 參考類別的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="4fcf0-110">擴展類別 ID 的指標。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fcf0-111">備註</span><span class="sxs-lookup"><span data-stu-id="4fcf0-111">Remarks</span></span>  

 <span data-ttu-id="4fcf0-112">此方法已淘汰;相反地，請 `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` 針對所有類型使用。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fcf0-113">需求</span><span class="sxs-lookup"><span data-stu-id="4fcf0-113">Requirements</span></span>  

 <span data-ttu-id="4fcf0-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4fcf0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fcf0-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4fcf0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4fcf0-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fcf0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fcf0-117">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="4fcf0-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcf0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fcf0-118">See also</span></span>

- [<span data-ttu-id="4fcf0-119">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="4fcf0-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
