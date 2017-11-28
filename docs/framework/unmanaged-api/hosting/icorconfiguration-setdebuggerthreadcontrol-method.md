---
title: "ICorConfiguration::SetDebuggerThreadControl 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4716e814c352fceacd8b949c2670058cf8a03bf1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="6eb4c-102">ICorConfiguration::SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="6eb4c-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="6eb4c-103">設定偵錯服務會針對偵錯呼叫為 common language runtime (CLR) 執行緒會封鎖及解除封鎖的回呼介面。</span><span class="sxs-lookup"><span data-stu-id="6eb4c-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6eb4c-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6eb4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6eb4c-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="6eb4c-106">[in]指標[IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)通知主機有關的封鎖和解除封鎖執行緒偵錯服務的物件。</span><span class="sxs-lookup"><span data-stu-id="6eb4c-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb4c-107">需求</span><span class="sxs-lookup"><span data-stu-id="6eb4c-107">Requirements</span></span>  
 <span data-ttu-id="6eb4c-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb4c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb4c-109">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6eb4c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6eb4c-110">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6eb4c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb4c-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb4c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb4c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb4c-112">See Also</span></span>  
 [<span data-ttu-id="6eb4c-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="6eb4c-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
