---
title: "ICorProfilerCallback::AssemblyLoadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48453532177b1e619f4f863e7297345566637d4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="8bc05-102">ICorProfilerCallback::AssemblyLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8bc05-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="8bc05-103">通知分析工具正在載入組件。</span><span class="sxs-lookup"><span data-stu-id="8bc05-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc05-104">語法</span><span class="sxs-lookup"><span data-stu-id="8bc05-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bc05-105">參數</span><span class="sxs-lookup"><span data-stu-id="8bc05-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="8bc05-106">[in]識別要載入的組件。</span><span class="sxs-lookup"><span data-stu-id="8bc05-106">[in] Identifies the assembly that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bc05-107">備註</span><span class="sxs-lookup"><span data-stu-id="8bc05-107">Remarks</span></span>  
 <span data-ttu-id="8bc05-108">值`assemblyId`不正確的資訊要求，直到[icorprofilercallback:: Assemblyloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="8bc05-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bc05-109">需求</span><span class="sxs-lookup"><span data-stu-id="8bc05-109">Requirements</span></span>  
 <span data-ttu-id="8bc05-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8bc05-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bc05-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8bc05-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8bc05-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bc05-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bc05-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bc05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bc05-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8bc05-114">See Also</span></span>  
 [<span data-ttu-id="8bc05-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8bc05-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
