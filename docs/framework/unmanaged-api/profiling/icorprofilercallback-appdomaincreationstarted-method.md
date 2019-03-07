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
ms.openlocfilehash: 2bffa383734a96a32595b018fd6d9b3dc62d5526
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484754"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="a3b83-102">ICorProfilerCallback::AppDomainCreationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a3b83-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>
<span data-ttu-id="a3b83-103">正在建立應用程式定義域會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="a3b83-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3b83-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3b83-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3b83-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3b83-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="a3b83-106">[in]識別正在建立的網域。</span><span class="sxs-lookup"><span data-stu-id="a3b83-106">[in] Identifies the domain which is being created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3b83-107">備註</span><span class="sxs-lookup"><span data-stu-id="a3b83-107">Remarks</span></span>  
 <span data-ttu-id="a3b83-108">識別碼不是有效的任何資訊要求，直到[icorprofilercallback:: Appdomaincreationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="a3b83-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3b83-109">需求</span><span class="sxs-lookup"><span data-stu-id="a3b83-109">Requirements</span></span>  
 <span data-ttu-id="a3b83-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a3b83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3b83-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3b83-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3b83-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3b83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3b83-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3b83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b83-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3b83-114">See also</span></span>
- [<span data-ttu-id="a3b83-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a3b83-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
