---
title: ICorProfilerCallback::AssemblyLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ace66630176149a18a174fad24f782a289b0e9d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763008"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="77e5d-102">ICorProfilerCallback::AssemblyLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="77e5d-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="77e5d-103">通知分析工具會在載入的組件。</span><span class="sxs-lookup"><span data-stu-id="77e5d-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77e5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="77e5d-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77e5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="77e5d-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="77e5d-106">[in]識別所要載入的組件。</span><span class="sxs-lookup"><span data-stu-id="77e5d-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77e5d-107">備註</span><span class="sxs-lookup"><span data-stu-id="77e5d-107">Remarks</span></span>  
 <span data-ttu-id="77e5d-108">值`assemblyId`資訊要求之前無效[icorprofilercallback:: Assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="77e5d-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77e5d-109">需求</span><span class="sxs-lookup"><span data-stu-id="77e5d-109">Requirements</span></span>  
 <span data-ttu-id="77e5d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77e5d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77e5d-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77e5d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77e5d-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77e5d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77e5d-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77e5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77e5d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77e5d-114">See also</span></span>

- [<span data-ttu-id="77e5d-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="77e5d-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
