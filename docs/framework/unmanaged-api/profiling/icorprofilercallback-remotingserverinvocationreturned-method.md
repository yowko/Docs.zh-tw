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
ms.openlocfilehash: 354736061a2c50b7db16070c3d4ff9c2548d394d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499944"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="06169-102">ICorProfilerCallback::RemotingServerInvocationReturned 方法</span><span class="sxs-lookup"><span data-stu-id="06169-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="06169-103">通知分析工具，進程已完成叫用方法以回應遠端方法調用要求。</span><span class="sxs-lookup"><span data-stu-id="06169-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06169-104">語法</span><span class="sxs-lookup"><span data-stu-id="06169-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="06169-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="06169-105">Requirements</span></span>  
 <span data-ttu-id="06169-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06169-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06169-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06169-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06169-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06169-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06169-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06169-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06169-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06169-110">See also</span></span>

- [<span data-ttu-id="06169-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="06169-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
