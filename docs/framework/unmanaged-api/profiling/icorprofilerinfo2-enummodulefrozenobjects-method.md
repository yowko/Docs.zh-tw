---
title: ICorProfilerInfo2::EnumModuleFrozenObjects 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.EnumModuleFrozenObjects
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::EnumModuleFrozenObjects
helpviewer_keywords:
- EnumModuleFrozenObjects method [.NET Framework profiling]
- ICorProfilerInfo2::EnumModuleFrozenObjects method [.NET Framework profiling]
ms.assetid: 920b6483-7064-4d64-8613-fcc38ccf9b1e
topic_type:
- apiref
ms.openlocfilehash: 1fe44f8f84c079e920c8c82fb9d52d1980d3b852
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497201"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="79c78-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="79c78-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="79c78-103">取得列舉值，允許在指定模組中的凍結物件上反覆運算。這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="79c78-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c78-104">語法</span><span class="sxs-lookup"><span data-stu-id="79c78-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c78-105">參數</span><span class="sxs-lookup"><span data-stu-id="79c78-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="79c78-106">在包含要列舉之凍結物件的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="79c78-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="79c78-107">脫銷[ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md)介面位址的指標，可列舉凍結的物件。</span><span class="sxs-lookup"><span data-stu-id="79c78-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c78-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="79c78-108">Requirements</span></span>  
 <span data-ttu-id="79c78-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79c78-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c78-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79c78-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79c78-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79c78-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c78-112">**.NET Framework 版本：** 3.5、3.0 SP1、3.0、2.0 SP1、2。0</span><span class="sxs-lookup"><span data-stu-id="79c78-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c78-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79c78-113">See also</span></span>

- [<span data-ttu-id="79c78-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="79c78-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="79c78-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="79c78-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
