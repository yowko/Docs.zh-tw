---
title: ICorProfilerCallback::AppDomainShutdownStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownStarted
helpviewer_keywords:
- AppDomainShutdownStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownStarted method [.NET Framework profiling]
ms.assetid: d23a3408-b525-4aec-a186-2ac7ca65d7a4
topic_type:
- apiref
ms.openlocfilehash: 1b973cdeaffbec0dad1f2d082c44e8001647fdcc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500451"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="0659e-102">ICorProfilerCallback::AppDomainShutdownStarted 方法</span><span class="sxs-lookup"><span data-stu-id="0659e-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="0659e-103">通知分析工具，應用程式域正在從進程中卸載。</span><span class="sxs-lookup"><span data-stu-id="0659e-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0659e-104">語法</span><span class="sxs-lookup"><span data-stu-id="0659e-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0659e-105">參數</span><span class="sxs-lookup"><span data-stu-id="0659e-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="0659e-106">\[在中，識別用來儲存應用程式元件的網域。</span><span class="sxs-lookup"><span data-stu-id="0659e-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="0659e-107">備註</span><span class="sxs-lookup"><span data-stu-id="0659e-107">Remarks</span></span>  
 <span data-ttu-id="0659e-108">在方法傳回之後，的值 `appDomainId` 對任何資訊要求而言都是不正確 `AppDomainShutdownStarted` ，這是 profiler 取得此應用程式域相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="0659e-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0659e-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="0659e-109">Requirements</span></span>  
 <span data-ttu-id="0659e-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0659e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0659e-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0659e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0659e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0659e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0659e-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0659e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0659e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0659e-114">See also</span></span>

- [<span data-ttu-id="0659e-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0659e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
