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
ms.openlocfilehash: fd1e5daada8793e94980afc5f0cf509915bd288e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450924"
---
# <a name="icorprofilercallbackappdomainshutdownstarted-method"></a><span data-ttu-id="1cc05-102">ICorProfilerCallback::AppDomainShutdownStarted 方法</span><span class="sxs-lookup"><span data-stu-id="1cc05-102">ICorProfilerCallback::AppDomainShutdownStarted Method</span></span>
<span data-ttu-id="1cc05-103">通知分析工具，應用程式定義域正在卸載的處理程序。</span><span class="sxs-lookup"><span data-stu-id="1cc05-103">Notifies the profiler that an application domain is being unloaded from a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc05-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cc05-104">Syntax</span></span>  
  
```  
HRESULT AppDomainShutdownStarted(  
    [in] AppDomainID appDomainId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cc05-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cc05-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="1cc05-106">[in]識別在儲存應用程式的組件所在的網域。</span><span class="sxs-lookup"><span data-stu-id="1cc05-106">[in] Identifies the domain in which the application's assemblies are stored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cc05-107">備註</span><span class="sxs-lookup"><span data-stu-id="1cc05-107">Remarks</span></span>  
 <span data-ttu-id="1cc05-108">值`appDomainId`不是有效的任何資訊的要求之後`AppDomainShutdownStarted`方法會傳回-這是程式碼剖析工具來取得這個應用程式定義域的相關資訊的最後機會。</span><span class="sxs-lookup"><span data-stu-id="1cc05-108">The value of `appDomainId` is not valid for any information request after the `AppDomainShutdownStarted` method returns — this is the profiler's last chance to get information about this application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cc05-109">需求</span><span class="sxs-lookup"><span data-stu-id="1cc05-109">Requirements</span></span>  
 <span data-ttu-id="1cc05-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cc05-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc05-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1cc05-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cc05-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cc05-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cc05-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc05-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc05-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc05-114">See Also</span></span>  
 [<span data-ttu-id="1cc05-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1cc05-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
