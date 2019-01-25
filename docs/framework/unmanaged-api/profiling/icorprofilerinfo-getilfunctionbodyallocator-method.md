---
title: ICorProfilerInfo::GetILFunctionBodyAllocator 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae8b209ad03594cb77029193b0e9dec773a6e02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603322"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a><span data-ttu-id="ed79d-102">ICorProfilerInfo::GetILFunctionBodyAllocator 方法</span><span class="sxs-lookup"><span data-stu-id="ed79d-102">ICorProfilerInfo::GetILFunctionBodyAllocator Method</span></span>
<span data-ttu-id="ed79d-103">取得的介面會提供方法來配置記憶體來用於交換的 Microsoft intermediate language (MSIL) 程式碼中的方法主體。</span><span class="sxs-lookup"><span data-stu-id="ed79d-103">Gets an interface that provides a method to allocate memory to be used for swapping out the body of a method in Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed79d-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed79d-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ed79d-105">參數</span><span class="sxs-lookup"><span data-stu-id="ed79d-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="ed79d-106">[in]此方法所在的模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="ed79d-106">[in] The ID of the module in which the method resides.</span></span>  
  
 `ppMalloc`  
 <span data-ttu-id="ed79d-107">[out]指標[IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)介面，可提供方法來配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="ed79d-107">[out] A pointer to an [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface that provides a method to allocate the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed79d-108">備註</span><span class="sxs-lookup"><span data-stu-id="ed79d-108">Remarks</span></span>  
 <span data-ttu-id="ed79d-109">方法主體中的 MSIL 程式碼必須位於為相對於載入的模組，這表示，它會遵循內 4 GB 的模組相對虛擬位址 (RVA)。</span><span class="sxs-lookup"><span data-stu-id="ed79d-109">A method body in MSIL code must be located as a relative virtual address (RVA), relative to the loaded module, which means that it follows the module within 4 GB.</span></span> <span data-ttu-id="ed79d-110">為了方便的工具，以交換出方法的主體`GetILFunctionBodyAllocator`方法可確保該記憶體配置該範圍內。</span><span class="sxs-lookup"><span data-stu-id="ed79d-110">To make it easier for a tool to swap out the body of a method, the `GetILFunctionBodyAllocator` method ensures that memory is allocated within that range.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed79d-111">需求</span><span class="sxs-lookup"><span data-stu-id="ed79d-111">Requirements</span></span>  
 <span data-ttu-id="ed79d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed79d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed79d-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ed79d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed79d-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed79d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed79d-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed79d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed79d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed79d-116">See also</span></span>
- [<span data-ttu-id="ed79d-117">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="ed79d-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
