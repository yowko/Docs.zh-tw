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
ms.openlocfilehash: f43ee6d9a3832fca1766ec27c9f02d1aab2f5b8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127764"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="d5b21-102">ICorConfiguration::SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="d5b21-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="d5b21-103">設定回呼介面，用於針對非執行時間工作排程執行緒，否則會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d5b21-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b21-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5b21-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b21-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5b21-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="d5b21-106">在[IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)物件的指標，會通知主機有關非執行時間工作的執行緒暫停。</span><span class="sxs-lookup"><span data-stu-id="d5b21-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b21-107">備註</span><span class="sxs-lookup"><span data-stu-id="d5b21-107">Remarks</span></span>  
 <span data-ttu-id="d5b21-108">主機可以在[IGCThreadControl：： ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)回呼中選擇是否要重新排定執行緒。</span><span class="sxs-lookup"><span data-stu-id="d5b21-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b21-109">需求</span><span class="sxs-lookup"><span data-stu-id="d5b21-109">Requirements</span></span>  
 <span data-ttu-id="d5b21-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5b21-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b21-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="d5b21-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5b21-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d5b21-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5b21-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b21-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b21-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d5b21-114">See also</span></span>

- [<span data-ttu-id="d5b21-115">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="d5b21-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
