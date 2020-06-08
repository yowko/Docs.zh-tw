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
ms.openlocfilehash: 3725b73ab55f6e4dc789a1fde8d1224695a174d7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499931"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="0bc18-102">ICorProfilerCallback::RemotingServerInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0bc18-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="0bc18-103">通知分析工具，進程正在叫用方法以回應遠端方法調用要求。</span><span class="sxs-lookup"><span data-stu-id="0bc18-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc18-104">語法</span><span class="sxs-lookup"><span data-stu-id="0bc18-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0bc18-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="0bc18-105">Requirements</span></span>  
 <span data-ttu-id="0bc18-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc18-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bc18-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0bc18-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bc18-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bc18-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bc18-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bc18-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc18-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bc18-110">See also</span></span>

- [<span data-ttu-id="0bc18-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0bc18-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
