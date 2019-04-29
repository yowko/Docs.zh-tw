---
title: IDebuggerThreadControl::StartBlockingForDebugger 方法
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc94c2de1a14842cc017e5c4ef6023154c20f2a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699899"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="43cd2-102">IDebuggerThreadControl::StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="43cd2-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="43cd2-103">主應用程式的偵錯服務即將開始封鎖所有執行緒。</span><span class="sxs-lookup"><span data-stu-id="43cd2-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43cd2-104">語法</span><span class="sxs-lookup"><span data-stu-id="43cd2-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43cd2-105">參數</span><span class="sxs-lookup"><span data-stu-id="43cd2-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="43cd2-106">[in]保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="43cd2-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43cd2-107">備註</span><span class="sxs-lookup"><span data-stu-id="43cd2-107">Remarks</span></span>  
 <span data-ttu-id="43cd2-108">`StartBlockingForDebugger`無法在執行階段的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="43cd2-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43cd2-109">需求</span><span class="sxs-lookup"><span data-stu-id="43cd2-109">Requirements</span></span>  
 <span data-ttu-id="43cd2-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="43cd2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43cd2-111">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43cd2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43cd2-112">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="43cd2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43cd2-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43cd2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43cd2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43cd2-114">See also</span></span>

- [<span data-ttu-id="43cd2-115">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="43cd2-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
