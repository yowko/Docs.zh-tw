---
title: ICorConfiguration::SetGCThreadControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93b52e0faef0fa3cc22283d6b46c5fe5153c3eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779869"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="a804d-102">ICorConfiguration::SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="a804d-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="a804d-103">設定排程執行緒非執行階段工作，否則會封鎖記憶體回收的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="a804d-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a804d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a804d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a804d-105">參數</span><span class="sxs-lookup"><span data-stu-id="a804d-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="a804d-106">[in]指標[IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)通知主機有關暫停的執行緒是否有非執行階段工作的物件。</span><span class="sxs-lookup"><span data-stu-id="a804d-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a804d-107">備註</span><span class="sxs-lookup"><span data-stu-id="a804d-107">Remarks</span></span>  
 <span data-ttu-id="a804d-108">主機可以選擇內[igcthreadcontrol:: Threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)回呼是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="a804d-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a804d-109">需求</span><span class="sxs-lookup"><span data-stu-id="a804d-109">Requirements</span></span>  
 <span data-ttu-id="a804d-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a804d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a804d-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a804d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a804d-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a804d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a804d-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a804d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a804d-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a804d-114">See also</span></span>

- [<span data-ttu-id="a804d-115">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="a804d-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
