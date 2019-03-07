---
title: ICorConfiguration::SetDebuggerThreadControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cecbbd7509fcd4f79aeb6e2711e8b7604c2f3a9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489685"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="847bd-102">ICorConfiguration::SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="847bd-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="847bd-103">設定偵錯的服務會針對偵錯呼叫隨著 common language runtime (CLR) 執行緒的封鎖和解除封鎖的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="847bd-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="847bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="847bd-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="847bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="847bd-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="847bd-106">[in]指標[IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)通知主機有關的封鎖和解除封鎖執行緒的偵錯服務的物件。</span><span class="sxs-lookup"><span data-stu-id="847bd-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="847bd-107">需求</span><span class="sxs-lookup"><span data-stu-id="847bd-107">Requirements</span></span>  
 <span data-ttu-id="847bd-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="847bd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="847bd-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="847bd-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="847bd-110">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="847bd-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="847bd-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="847bd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="847bd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="847bd-112">See also</span></span>
- [<span data-ttu-id="847bd-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="847bd-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
