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
ms.openlocfilehash: 72f7bee79e74c69acff90861ceada8a91afe2157
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134921"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="2a4eb-102">IDebuggerThreadControl::StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="2a4eb-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="2a4eb-103">通知主機偵錯工具即將開始封鎖所有線程。</span><span class="sxs-lookup"><span data-stu-id="2a4eb-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4eb-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a4eb-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a4eb-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a4eb-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="2a4eb-106">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="2a4eb-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a4eb-107">備註</span><span class="sxs-lookup"><span data-stu-id="2a4eb-107">Remarks</span></span>  
 <span data-ttu-id="2a4eb-108">可以在運行時間表程上呼叫 `StartBlockingForDebugger` 方法。</span><span class="sxs-lookup"><span data-stu-id="2a4eb-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a4eb-109">需求</span><span class="sxs-lookup"><span data-stu-id="2a4eb-109">Requirements</span></span>  
 <span data-ttu-id="2a4eb-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a4eb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4eb-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="2a4eb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a4eb-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2a4eb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a4eb-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4eb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="2a4eb-114">See also</span></span>

- [<span data-ttu-id="2a4eb-115">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="2a4eb-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
