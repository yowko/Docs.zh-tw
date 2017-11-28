---
title: "ICorProfilerCallback::RemotingServerInvocationStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingServerInvocationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c4e1fd36c7c6a1a3c4df8dfa233206de51676af1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="4c4b3-102">ICorProfilerCallback::RemotingServerInvocationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="4c4b3-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="4c4b3-103">通知分析工具處理程序叫用之遠端方法叫用要求回應中的方法。</span><span class="sxs-lookup"><span data-stu-id="4c4b3-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c4b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c4b3-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="4c4b3-105">需求</span><span class="sxs-lookup"><span data-stu-id="4c4b3-105">Requirements</span></span>  
 <span data-ttu-id="4c4b3-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c4b3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c4b3-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c4b3-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c4b3-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c4b3-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c4b3-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c4b3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c4b3-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c4b3-110">See Also</span></span>  
 [<span data-ttu-id="4c4b3-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4c4b3-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
