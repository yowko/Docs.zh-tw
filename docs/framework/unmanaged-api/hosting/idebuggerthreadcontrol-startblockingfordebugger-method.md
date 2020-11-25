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
ms.openlocfilehash: 1e0cb52a6b9f03209256e5398415b4ec632fb5e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705498"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="59e70-102">IDebuggerThreadControl::StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="59e70-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="59e70-103">通知主機偵錯工具即將開始封鎖所有線程。</span><span class="sxs-lookup"><span data-stu-id="59e70-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e70-104">語法</span><span class="sxs-lookup"><span data-stu-id="59e70-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59e70-105">參數</span><span class="sxs-lookup"><span data-stu-id="59e70-105">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="59e70-106">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="59e70-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59e70-107">備註</span><span class="sxs-lookup"><span data-stu-id="59e70-107">Remarks</span></span>  

 <span data-ttu-id="59e70-108">`StartBlockingForDebugger`方法可以在運行時間表程上呼叫。</span><span class="sxs-lookup"><span data-stu-id="59e70-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59e70-109">需求</span><span class="sxs-lookup"><span data-stu-id="59e70-109">Requirements</span></span>  

 <span data-ttu-id="59e70-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59e70-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59e70-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="59e70-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="59e70-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="59e70-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59e70-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59e70-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e70-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59e70-114">See also</span></span>

- [<span data-ttu-id="59e70-115">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="59e70-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
