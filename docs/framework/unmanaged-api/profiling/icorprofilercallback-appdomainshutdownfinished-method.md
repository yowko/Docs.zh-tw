---
title: ICorProfilerCallback::AppDomainShutdownFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d927bd21903bda6fd8a34992145eb495a3342382
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081953"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="7f51b-102">ICorProfilerCallback::AppDomainShutdownFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7f51b-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="7f51b-103">應用程式定義域已卸載的程序會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="7f51b-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f51b-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f51b-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f51b-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f51b-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="7f51b-106">[in]識別儲存應用程式的組件所在的網域。</span><span class="sxs-lookup"><span data-stu-id="7f51b-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7f51b-107">[in]HRESULT，指出是否在應用程式定義域已卸載成功。</span><span class="sxs-lookup"><span data-stu-id="7f51b-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f51b-108">備註</span><span class="sxs-lookup"><span data-stu-id="7f51b-108">Remarks</span></span>  
 <span data-ttu-id="7f51b-109">值`appDomainId`不是有效資訊要求之後[icorprofilercallback:: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="7f51b-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="7f51b-110">卸載應用程式定義域的某些部分可能會繼續之後`AppDomainCreationFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="7f51b-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="7f51b-111">失敗 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="7f51b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="7f51b-112">不過，成功的 HRESULT 中`hrStatus`僅會指示已成功卸載應用程式定義域的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="7f51b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f51b-113">需求</span><span class="sxs-lookup"><span data-stu-id="7f51b-113">Requirements</span></span>  
 <span data-ttu-id="7f51b-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f51b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f51b-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f51b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f51b-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f51b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7f51b-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7f51b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f51b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f51b-118">See also</span></span>

- [<span data-ttu-id="7f51b-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7f51b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
