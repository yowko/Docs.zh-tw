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
ms.openlocfilehash: 3e044a9dedf96025981c1a77471c6abedfc26420
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762380"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="8c575-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="8c575-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="8c575-103">取得可反覆項目讓您透過指定的模組中的凍結物件的列舉值。這個方法已經過時。</span><span class="sxs-lookup"><span data-stu-id="8c575-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c575-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c575-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c575-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c575-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8c575-106">[in]包含要列舉的凍結的物件模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8c575-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="8c575-107">[out]位址指標[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面，其中會列舉凍結的物件。</span><span class="sxs-lookup"><span data-stu-id="8c575-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c575-108">需求</span><span class="sxs-lookup"><span data-stu-id="8c575-108">Requirements</span></span>  
 <span data-ttu-id="8c575-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c575-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c575-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8c575-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c575-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c575-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c575-112">**.NET framework 版本：** 3.5、 3.0 SP1，3.0，2.0 SP1，2.0</span><span class="sxs-lookup"><span data-stu-id="8c575-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c575-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c575-113">See also</span></span>

- [<span data-ttu-id="8c575-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="8c575-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="8c575-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="8c575-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
