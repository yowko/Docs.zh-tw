---
title: "ICorProfilerCallback::RemotingServerInvocationReturned 方法"
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
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dac859c52f5e85173bb28821672a6437f3e0718f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="36dba-102">ICorProfilerCallback::RemotingServerInvocationReturned 方法</span><span class="sxs-lookup"><span data-stu-id="36dba-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="36dba-103">通知分析工具處理序已完成叫用之遠端方法叫用要求回應中的方法。</span><span class="sxs-lookup"><span data-stu-id="36dba-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36dba-104">語法</span><span class="sxs-lookup"><span data-stu-id="36dba-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="36dba-105">需求</span><span class="sxs-lookup"><span data-stu-id="36dba-105">Requirements</span></span>  
 <span data-ttu-id="36dba-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36dba-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36dba-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36dba-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36dba-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36dba-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36dba-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36dba-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36dba-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="36dba-110">See Also</span></span>  
 [<span data-ttu-id="36dba-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="36dba-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
