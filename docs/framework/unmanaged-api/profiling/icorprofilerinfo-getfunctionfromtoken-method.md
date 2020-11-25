---
title: ICorProfilerInfo::GetFunctionFromToken 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionFromToken method [.NET Framework profiling]
- GetFunctionFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0eed759f-cce8-405d-88dc-9ee293a38928
topic_type:
- apiref
ms.openlocfilehash: 9c7f01d2e462ad1cb0532be6f369c3118a4deb6a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722488"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="bc597-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="bc597-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>

<span data-ttu-id="bc597-103">取得函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bc597-103">Gets the ID of a function.</span></span> <span data-ttu-id="bc597-104">此方法在 .NET Framework 版本2.0 中已淘汰。</span><span class="sxs-lookup"><span data-stu-id="bc597-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bc597-105">請改用 [ICorProfilerInfo2：： GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="bc597-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc597-106">語法</span><span class="sxs-lookup"><span data-stu-id="bc597-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="bc597-107">備註</span><span class="sxs-lookup"><span data-stu-id="bc597-107">Remarks</span></span>  

 <span data-ttu-id="bc597-108">`GetFunctionFromToken`方法不適用於泛型函式或泛型型別中的函式，它現在已過時。</span><span class="sxs-lookup"><span data-stu-id="bc597-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="bc597-109">用於 `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` 所有函數。</span><span class="sxs-lookup"><span data-stu-id="bc597-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc597-110">需求</span><span class="sxs-lookup"><span data-stu-id="bc597-110">Requirements</span></span>  

 <span data-ttu-id="bc597-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc597-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc597-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bc597-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc597-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc597-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc597-114">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="bc597-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc597-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc597-115">See also</span></span>

- [<span data-ttu-id="bc597-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="bc597-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
