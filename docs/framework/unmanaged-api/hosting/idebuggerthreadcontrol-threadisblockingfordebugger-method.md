---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
ms.openlocfilehash: 8c2741d7db60781fef12293f3be0b515a55b7885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705501"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="a5ed8-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="a5ed8-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="a5ed8-103">通知主機傳送此回呼的執行緒即將在偵錯工具中封鎖。</span><span class="sxs-lookup"><span data-stu-id="a5ed8-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5ed8-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5ed8-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a5ed8-105">備註</span><span class="sxs-lookup"><span data-stu-id="a5ed8-105">Remarks</span></span>  

 <span data-ttu-id="a5ed8-106">`ThreadIsBlockingForDebugger`方法一律會在運行時間表程上呼叫。</span><span class="sxs-lookup"><span data-stu-id="a5ed8-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="a5ed8-107">`ThreadIsBlockingForDebugger`方法可讓主機線上程封鎖時有機會執行另一個動作。</span><span class="sxs-lookup"><span data-stu-id="a5ed8-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5ed8-108">需求</span><span class="sxs-lookup"><span data-stu-id="a5ed8-108">Requirements</span></span>  

 <span data-ttu-id="a5ed8-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5ed8-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5ed8-110">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a5ed8-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5ed8-111">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a5ed8-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5ed8-112">**.Net Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5ed8-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5ed8-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5ed8-113">See also</span></span>

- [<span data-ttu-id="a5ed8-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a5ed8-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
