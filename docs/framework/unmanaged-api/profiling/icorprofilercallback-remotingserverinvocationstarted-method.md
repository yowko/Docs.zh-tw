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
ms.openlocfilehash: 3571b429c3733a07a74d50f69ecf8987d75b034f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865983"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="72aab-102">ICorProfilerCallback::RemotingServerInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="72aab-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="72aab-103">通知分析工具，進程正在叫用方法以回應遠端方法調用要求。</span><span class="sxs-lookup"><span data-stu-id="72aab-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72aab-104">語法</span><span class="sxs-lookup"><span data-stu-id="72aab-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="72aab-105">需求</span><span class="sxs-lookup"><span data-stu-id="72aab-105">Requirements</span></span>  
 <span data-ttu-id="72aab-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72aab-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72aab-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72aab-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72aab-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72aab-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72aab-109">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72aab-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72aab-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="72aab-110">See also</span></span>

- [<span data-ttu-id="72aab-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="72aab-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
