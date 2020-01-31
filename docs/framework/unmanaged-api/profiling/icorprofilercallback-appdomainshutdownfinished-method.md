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
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866672"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="fa4ce-102">ICorProfilerCallback::AppDomainShutdownFinished 方法</span><span class="sxs-lookup"><span data-stu-id="fa4ce-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="fa4ce-103">通知分析工具，應用程式域已從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa4ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa4ce-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa4ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa4ce-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="fa4ce-106">中的 \[] 可識別用來儲存應用程式元件的網域。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="fa4ce-107">\[in]） HRESULT，指出是否已成功卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="fa4ce-108">備註</span><span class="sxs-lookup"><span data-stu-id="fa4ce-108">Remarks</span></span>  
 <span data-ttu-id="fa4ce-109">[ICorProfilerCallback：： AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md)方法傳回之後，`appDomainId` 的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="fa4ce-110">卸載應用程式域的某些部分可能會在 `AppDomainCreationFinished` 回呼之後繼續進行。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="fa4ce-111">`hrStatus` 中的失敗 HRESULT 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="fa4ce-112">不過，`hrStatus` 中的成功 HRESULT 只會指出卸載應用程式域的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa4ce-113">需求</span><span class="sxs-lookup"><span data-stu-id="fa4ce-113">Requirements</span></span>  
 <span data-ttu-id="fa4ce-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa4ce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa4ce-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa4ce-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa4ce-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa4ce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa4ce-117">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa4ce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa4ce-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa4ce-118">See also</span></span>

- [<span data-ttu-id="fa4ce-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fa4ce-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
