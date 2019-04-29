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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f422e99a5f6a4153368304ff0b33bbc55381575a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597845"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="50928-102">ICorProfilerCallback::AppDomainShutdownStarted 方法</span><span class="sxs-lookup"><span data-stu-id="50928-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="50928-103">通知分析工具，應用程式定義域正在卸載的處理程序。</span><span class="sxs-lookup"><span data-stu-id="50928-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50928-104">語法</span><span class="sxs-lookup"><span data-stu-id="50928-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50928-105">參數</span><span class="sxs-lookup"><span data-stu-id="50928-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="50928-106">[in]識別儲存應用程式的組件所在的網域。</span><span class="sxs-lookup"><span data-stu-id="50928-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50928-107">備註</span><span class="sxs-lookup"><span data-stu-id="50928-107">Remarks</span></span>  
 <span data-ttu-id="50928-108">值`appDomainId`不是有效的任何資訊的要求之後`AppDomainShutdownStarted`方法會傳回 — 這是要取得這個應用程式定義域的相關資訊的分析工具的最後機會。</span><span class="sxs-lookup"><span data-stu-id="50928-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50928-109">需求</span><span class="sxs-lookup"><span data-stu-id="50928-109">Requirements</span></span>  
 <span data-ttu-id="50928-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50928-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50928-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50928-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50928-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50928-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50928-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50928-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50928-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50928-114">See also</span></span>

- [<span data-ttu-id="50928-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="50928-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
