---
title: ICorProfilerCallback::AppDomainCreationStarted 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98fac8630403107f96f2fa86e5bcc9b0e60d0d08
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737159"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="babf9-102">ICorProfilerCallback::AppDomainCreationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="babf9-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="babf9-103">正在建立應用程式定義域會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="babf9-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babf9-104">語法</span><span class="sxs-lookup"><span data-stu-id="babf9-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="babf9-105">參數</span><span class="sxs-lookup"><span data-stu-id="babf9-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="babf9-106">[in]識別正在建立的網域。</span><span class="sxs-lookup"><span data-stu-id="babf9-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="babf9-107">備註</span><span class="sxs-lookup"><span data-stu-id="babf9-107">Remarks</span></span>  
 <span data-ttu-id="babf9-108">識別碼不是有效的任何資訊要求，直到[icorprofilercallback:: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="babf9-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="babf9-109">需求</span><span class="sxs-lookup"><span data-stu-id="babf9-109">Requirements</span></span>  
 <span data-ttu-id="babf9-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="babf9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="babf9-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="babf9-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="babf9-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="babf9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="babf9-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="babf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babf9-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="babf9-114">See also</span></span>
- [<span data-ttu-id="babf9-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="babf9-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
