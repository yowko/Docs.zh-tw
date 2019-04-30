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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f4fb2292154a2660a2db3f0b3962fcf2114e385
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049605"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="63e59-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="63e59-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="63e59-103">取得函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="63e59-103">Gets the ID of a function.</span></span> <span data-ttu-id="63e59-104">這個方法是在.NET Framework 2.0 版中已過時。</span><span class="sxs-lookup"><span data-stu-id="63e59-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="63e59-105">使用[ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="63e59-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e59-106">語法</span><span class="sxs-lookup"><span data-stu-id="63e59-106">Syntax</span></span>  
  
```  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="63e59-107">備註</span><span class="sxs-lookup"><span data-stu-id="63e59-107">Remarks</span></span>  
 <span data-ttu-id="63e59-108">`GetFunctionFromToken`方法不適用於泛型函式或泛型型別中的函式; 它現在已過時。</span><span class="sxs-lookup"><span data-stu-id="63e59-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="63e59-109">使用`ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs`所有函式。</span><span class="sxs-lookup"><span data-stu-id="63e59-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63e59-110">需求</span><span class="sxs-lookup"><span data-stu-id="63e59-110">Requirements</span></span>  
 <span data-ttu-id="63e59-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63e59-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63e59-112">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="63e59-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="63e59-113">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63e59-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63e59-114">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="63e59-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e59-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63e59-115">See also</span></span>

- [<span data-ttu-id="63e59-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="63e59-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
