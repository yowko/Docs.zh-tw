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
ms.openlocfilehash: 18c3b6e840ec1f6cb1481c8d752e6399dcdae077
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498137"
---
# <a name="icorprofilerinfogetfunctionfromtoken-method"></a><span data-ttu-id="f7801-102">ICorProfilerInfo::GetFunctionFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="f7801-102">ICorProfilerInfo::GetFunctionFromToken Method</span></span>
<span data-ttu-id="f7801-103">取得函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f7801-103">Gets the ID of a function.</span></span> <span data-ttu-id="f7801-104">這個方法在 .NET Framework 版本2.0 中已過時。</span><span class="sxs-lookup"><span data-stu-id="f7801-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="f7801-105">請改用[ICorProfilerInfo2：： GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f7801-105">Use the [ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7801-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7801-106">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in]  ModuleID   moduleId,  
    [in]  mdToken    token,  
    [out] FunctionID *pFunctionId);  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7801-107">備註</span><span class="sxs-lookup"><span data-stu-id="f7801-107">Remarks</span></span>  
 <span data-ttu-id="f7801-108">方法不適用於泛型函式或泛型型別中的函式， `GetFunctionFromToken` 它現在已過時。</span><span class="sxs-lookup"><span data-stu-id="f7801-108">The `GetFunctionFromToken` method will not work for generic functions or functions in generic types; it is now obsolete.</span></span> <span data-ttu-id="f7801-109">用於 `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` 所有函式。</span><span class="sxs-lookup"><span data-stu-id="f7801-109">Use `ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs` for all functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7801-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="f7801-110">Requirements</span></span>  
 <span data-ttu-id="f7801-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7801-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7801-112">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7801-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7801-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7801-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7801-114">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="f7801-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7801-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7801-115">See also</span></span>

- [<span data-ttu-id="f7801-116">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="f7801-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
