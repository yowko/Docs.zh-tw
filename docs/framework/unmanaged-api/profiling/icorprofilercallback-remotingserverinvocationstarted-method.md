---
title: ICorProfilerCallback::RemotingServerInvocationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c9a4aa165057f1345de2c6f5bda80e4317d06c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221804"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="0da79-102">ICorProfilerCallback::RemotingServerInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0da79-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="0da79-103">通知分析工具處理程序會叫用遠端方法引動過程要求的回應中的方法。</span><span class="sxs-lookup"><span data-stu-id="0da79-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da79-104">語法</span><span class="sxs-lookup"><span data-stu-id="0da79-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0da79-105">需求</span><span class="sxs-lookup"><span data-stu-id="0da79-105">Requirements</span></span>  
 <span data-ttu-id="0da79-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0da79-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0da79-107">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0da79-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0da79-108">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0da79-108">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0da79-109">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0da79-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0da79-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0da79-110">See also</span></span>

- [<span data-ttu-id="0da79-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0da79-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
