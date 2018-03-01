---
title: "ICorProfilerCallback::AppDomainCreationStarted 方法"
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
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe9089438f64bff19439af76c3f5eaf18fc5d6d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="8b931-102">ICorProfilerCallback::AppDomainCreationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8b931-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="8b931-103">通知分析工具所建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="8b931-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b931-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b931-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8b931-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b931-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="8b931-106">[in]識別正在建立的網域。</span><span class="sxs-lookup"><span data-stu-id="8b931-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b931-107">備註</span><span class="sxs-lookup"><span data-stu-id="8b931-107">Remarks</span></span>  
 <span data-ttu-id="8b931-108">識別碼不是有效的任何資訊要求到[icorprofilercallback:: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b931-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b931-109">需求</span><span class="sxs-lookup"><span data-stu-id="8b931-109">Requirements</span></span>  
 <span data-ttu-id="8b931-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b931-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b931-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b931-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b931-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b931-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b931-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b931-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b931-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b931-114">See Also</span></span>  
 [<span data-ttu-id="8b931-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8b931-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
