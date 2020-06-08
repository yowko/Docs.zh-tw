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
ms.openlocfilehash: 722a1e0adea41a13ca25829c53372c29187b80bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500464"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a><span data-ttu-id="9e4b9-102">ICorProfilerCallback::AppDomainShutdownFinished 方法</span><span class="sxs-lookup"><span data-stu-id="9e4b9-102">ICorProfilerCallback::AppDomainShutdownFinished Method</span></span>
<span data-ttu-id="9e4b9-103">通知分析工具，應用程式域已從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-103">Notifies the profiler that an application domain has been unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e4b9-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e4b9-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e4b9-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e4b9-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="9e4b9-106">\[在中，識別用來儲存應用程式元件的網域。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

- `hrStatus`

  <span data-ttu-id="9e4b9-107">\[中的 HRESULT，指出是否已成功卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-107">\[in] An HRESULT that indicates whether the application domain was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="9e4b9-108">備註</span><span class="sxs-lookup"><span data-stu-id="9e4b9-108">Remarks</span></span>  
 <span data-ttu-id="9e4b9-109">在 `appDomainId` [ICorProfilerCallback：： AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md)方法傳回之後，的值對資訊要求而言是不正確。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-109">The value of `appDomainId` is not valid for an information request after the [ICorProfilerCallback::AppDomainShutdownStarted](icorprofilercallback-appdomainshutdownstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="9e4b9-110">卸載應用程式域的某些部分可能會在回呼之後繼續進行 `AppDomainCreationFinished` 。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-110">Some parts of unloading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="9e4b9-111">中的失敗 HRESULT `hrStatus` 表示失敗。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9e4b9-112">不過，中的成功 HRESULT `hrStatus` 只會指出卸載應用程式域的第一個部分已成功。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e4b9-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="9e4b9-113">Requirements</span></span>  
 <span data-ttu-id="9e4b9-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e4b9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e4b9-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e4b9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e4b9-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e4b9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e4b9-117">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e4b9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4b9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4b9-118">See also</span></span>

- [<span data-ttu-id="9e4b9-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9e4b9-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
