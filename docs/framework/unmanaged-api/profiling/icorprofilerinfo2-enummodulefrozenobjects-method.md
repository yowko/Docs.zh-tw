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
ms.openlocfilehash: 77b07dae5b53db58b3628f677be1714e66ac18ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455253"
---
# <a name="icorprofilerinfo2enummodulefrozenobjects-method"></a><span data-ttu-id="ebf85-102">ICorProfilerInfo2::EnumModuleFrozenObjects 方法</span><span class="sxs-lookup"><span data-stu-id="ebf85-102">ICorProfilerInfo2::EnumModuleFrozenObjects Method</span></span>
<span data-ttu-id="ebf85-103">取得允許反覆項目所指定模組中凍結物件的列舉值。這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="ebf85-103">Gets an enumerator that allows iteration over the frozen objects in the specified module.This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf85-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebf85-104">Syntax</span></span>  
  
```  
HRESULT EnumModuleFrozenObjects(  
    [in] ModuleID moduleID,  
    [out] ICorProfilerObjectEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebf85-105">參數</span><span class="sxs-lookup"><span data-stu-id="ebf85-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="ebf85-106">[in]包含要列舉的凍結的物件模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ebf85-106">[in] The ID of the module that contains the frozen objects to be enumerated.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="ebf85-107">[out]位址指標[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)介面，其中會列舉凍結的物件。</span><span class="sxs-lookup"><span data-stu-id="ebf85-107">[out] A pointer to the address of an [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface, which enumerates the frozen objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf85-108">需求</span><span class="sxs-lookup"><span data-stu-id="ebf85-108">Requirements</span></span>  
 <span data-ttu-id="ebf85-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ebf85-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf85-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebf85-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebf85-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebf85-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebf85-112">**.NET framework 版本：** 3.5、 3.0 SP1、 3.0、 2.0 SP1、 2.0</span><span class="sxs-lookup"><span data-stu-id="ebf85-112">**.NET Framework Versions:** 3.5, 3.0 SP1, 3.0, 2.0 SP1, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf85-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf85-113">See Also</span></span>  
 [<span data-ttu-id="ebf85-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ebf85-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ebf85-115">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="ebf85-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
