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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74517e034af6a1e4dfb8e4b28c2fec55a3d8de8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041154"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="2e177-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="2e177-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="2e177-103">取得可反覆項目讓您透過指定的模組中的凍結物件的列舉值。這個方法已經過時。</span><span class="sxs-lookup"><span data-stu-id="2e177-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e177-104">語法</span><span class="sxs-lookup"><span data-stu-id="2e177-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e177-105">參數</span><span class="sxs-lookup"><span data-stu-id="2e177-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="2e177-106">[in]包含要列舉的凍結的物件模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2e177-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="2e177-107">[out]位址指標[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面，其中會列舉凍結的物件。</span><span class="sxs-lookup"><span data-stu-id="2e177-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e177-108">需求</span><span class="sxs-lookup"><span data-stu-id="2e177-108">Requirements</span></span>  
 <span data-ttu-id="2e177-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2e177-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e177-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e177-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e177-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e177-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e177-112">**.NET framework 版本：** 3.5、 3.0 SP1，3.0，2.0 SP1，2.0</span><span class="sxs-lookup"><span data-stu-id="2e177-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e177-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e177-113">See also</span></span>

- [<span data-ttu-id="2e177-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="2e177-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2e177-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="2e177-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
