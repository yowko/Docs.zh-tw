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
ms.openlocfilehash: 2b2d619c5940376806e9873a528b4f08886593e9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863552"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="3d9fb-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="3d9fb-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="3d9fb-103">取得函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-103">Gets the ID of a function.</span></span> <span data-ttu-id="3d9fb-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3d9fb-105">請改用[ICorProfilerInfo2：： GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9fb-106">語法</span><span class="sxs-lookup"><span data-stu-id="3d9fb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3d9fb-107">備註</span><span class="sxs-lookup"><span data-stu-id="3d9fb-107">Remarks</span></span>  
 <span data-ttu-id="3d9fb-108">`GetFunctionFromToken` 的方法不適用於泛型函式或泛型型別中的函數。它現在已過時。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="3d9fb-109">針對所有功能使用 `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9fb-110">需求</span><span class="sxs-lookup"><span data-stu-id="3d9fb-110">Requirements</span></span>  
 <span data-ttu-id="3d9fb-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d9fb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d9fb-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d9fb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d9fb-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d9fb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d9fb-114">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="3d9fb-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9fb-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d9fb-115">See also</span></span>

- [<span data-ttu-id="3d9fb-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="3d9fb-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
