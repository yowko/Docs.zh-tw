---
title: ICorProfilerCallback::RemotingServerInvocationReturned 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00f5fd44d340a76200537871a9860f67601b66d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208705"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="8b50d-102">ICorProfilerCallback::RemotingServerInvocationReturned 方法</span><span class="sxs-lookup"><span data-stu-id="8b50d-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="8b50d-103">通知分析工具處理序已完成叫用遠端方法引動過程要求的回應中的方法。</span><span class="sxs-lookup"><span data-stu-id="8b50d-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b50d-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b50d-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8b50d-105">需求</span><span class="sxs-lookup"><span data-stu-id="8b50d-105">Requirements</span></span>  
 <span data-ttu-id="8b50d-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b50d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b50d-107">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b50d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b50d-108">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b50d-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8b50d-109">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="8b50d-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b50d-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b50d-110">See also</span></span>

- [<span data-ttu-id="8b50d-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8b50d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
