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
ms.openlocfilehash: 3f9f8925630933e2247726f92a93cac67bdc55ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450485"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="36777-102">ICorProfilerCallback::AppDomainShutdownFinished 方法</span><span class="sxs-lookup"><span data-stu-id="36777-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="36777-103">通知分析工具，應用程式定義域已卸載的處理程序。</span><span class="sxs-lookup"><span data-stu-id="36777-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36777-104">語法</span><span class="sxs-lookup"><span data-stu-id="36777-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36777-105">參數</span><span class="sxs-lookup"><span data-stu-id="36777-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="36777-106">[in]識別在儲存應用程式的組件所在的網域。</span><span class="sxs-lookup"><span data-stu-id="36777-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="36777-107">[in]HRESULT，指出是否在應用程式定義域已卸載成功。</span><span class="sxs-lookup"><span data-stu-id="36777-107">[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36777-108">備註</span><span class="sxs-lookup"><span data-stu-id="36777-108">Remarks</span></span>  
 <span data-ttu-id="36777-109">值`appDomainId`不正確資訊要求之後[icorprofilercallback:: Appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)方法會傳回。</span><span class="sxs-lookup"><span data-stu-id="36777-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="36777-110">卸載應用程式定義域的某些部分可能會繼續之後`AppDomainCreationFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="36777-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="36777-111">失敗的 HRESULT 中`hrStatus`表示失敗。</span><span class="sxs-lookup"><span data-stu-id="36777-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="36777-112">不過，成功 HRESULT 中`hrStatus`只會指出已成功卸載應用程式定義域的第一個部分。</span><span class="sxs-lookup"><span data-stu-id="36777-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36777-113">需求</span><span class="sxs-lookup"><span data-stu-id="36777-113">Requirements</span></span>  
 <span data-ttu-id="36777-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36777-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36777-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36777-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="36777-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36777-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36777-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36777-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36777-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36777-118">See Also</span></span>  
 [<span data-ttu-id="36777-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="36777-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
