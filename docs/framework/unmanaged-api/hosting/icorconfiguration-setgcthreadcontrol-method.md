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
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135833"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="be092-102">ICorConfiguration::SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="be092-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="be092-103">設定排程執行緒非執行階段工作，否則會封鎖記憶體回收的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="be092-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be092-104">語法</span><span class="sxs-lookup"><span data-stu-id="be092-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be092-105">參數</span><span class="sxs-lookup"><span data-stu-id="be092-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="be092-106">[in]指標[IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)通知主機有關暫停的執行緒是否有非執行階段工作的物件。</span><span class="sxs-lookup"><span data-stu-id="be092-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be092-107">備註</span><span class="sxs-lookup"><span data-stu-id="be092-107">Remarks</span></span>  
 <span data-ttu-id="be092-108">主機可以選擇內[igcthreadcontrol:: Threadisblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)回呼是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="be092-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be092-109">需求</span><span class="sxs-lookup"><span data-stu-id="be092-109">Requirements</span></span>  
 <span data-ttu-id="be092-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be092-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be092-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be092-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be092-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="be092-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be092-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be092-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be092-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be092-114">See also</span></span>

- [<span data-ttu-id="be092-115">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="be092-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
