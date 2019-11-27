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
ms.openlocfilehash: 51e0c5b08b8a2ac3b8eaf38cdabd682078ba70c8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436045"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="00e5b-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="00e5b-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="00e5b-103">取得列舉值，允許在指定模組中的凍結物件上反覆運算。這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="00e5b-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e5b-104">語法</span><span class="sxs-lookup"><span data-stu-id="00e5b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00e5b-105">參數</span><span class="sxs-lookup"><span data-stu-id="00e5b-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="00e5b-106">在包含要列舉之凍結物件的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="00e5b-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="00e5b-107">脫銷[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面位址的指標，可列舉凍結的物件。</span><span class="sxs-lookup"><span data-stu-id="00e5b-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00e5b-108">需求</span><span class="sxs-lookup"><span data-stu-id="00e5b-108">Requirements</span></span>  
 <span data-ttu-id="00e5b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00e5b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e5b-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00e5b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00e5b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00e5b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00e5b-112">**.NET Framework 版本：** 3.5、3.0 SP1、3.0、2.0 SP1、2。0</span><span class="sxs-lookup"><span data-stu-id="00e5b-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e5b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00e5b-113">See also</span></span>

- [<span data-ttu-id="00e5b-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="00e5b-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="00e5b-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="00e5b-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
