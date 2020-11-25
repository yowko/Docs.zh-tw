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
ms.openlocfilehash: cb0b763059c787b8f3e93e6c46b0e7fb2f8f8b2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718458"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="7b514-102">ICorProfilerCallback::AppDomainShutdownStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7b514-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>

<span data-ttu-id="7b514-103">通知分析工具正在從進程卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="7b514-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b514-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b514-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b514-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b514-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="7b514-106">\[in] 識別用來儲存應用程式元件的網域。</span><span class="sxs-lookup"><span data-stu-id="7b514-106">\[in] Identifies the domain in which the application's assemblies are stored.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b514-107">備註</span><span class="sxs-lookup"><span data-stu-id="7b514-107">Remarks</span></span>  

 <span data-ttu-id="7b514-108">在方法傳回之後，的值對 `appDomainId` 任何資訊要求而言是不正確 `AppDomainShutdownStarted` ，這是 profiler 取得此應用程式域相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="7b514-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b514-109">需求</span><span class="sxs-lookup"><span data-stu-id="7b514-109">Requirements</span></span>  

 <span data-ttu-id="7b514-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b514-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b514-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b514-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b514-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b514-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b514-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b514-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b514-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b514-114">See also</span></span>

- [<span data-ttu-id="7b514-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7b514-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
