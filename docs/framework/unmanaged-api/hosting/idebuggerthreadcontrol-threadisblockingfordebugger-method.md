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
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805259"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="b0ea4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="b0ea4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="b0ea4-103">通知主機傳送此回呼的執行緒即將在偵錯工具中封鎖。</span><span class="sxs-lookup"><span data-stu-id="b0ea4-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0ea4-104">語法</span><span class="sxs-lookup"><span data-stu-id="b0ea4-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b0ea4-105">備註</span><span class="sxs-lookup"><span data-stu-id="b0ea4-105">Remarks</span></span>  
 <span data-ttu-id="b0ea4-106">`ThreadIsBlockingForDebugger`方法一律會在運行時間表程上呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0ea4-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="b0ea4-107">`ThreadIsBlockingForDebugger`方法可讓主機有機會線上程封鎖時執行另一個動作。</span><span class="sxs-lookup"><span data-stu-id="b0ea4-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0ea4-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="b0ea4-108">Requirements</span></span>  
 <span data-ttu-id="b0ea4-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0ea4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0ea4-110">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="b0ea4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0ea4-111">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b0ea4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0ea4-112">**.Net Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0ea4-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0ea4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0ea4-113">See also</span></span>

- [<span data-ttu-id="b0ea4-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="b0ea4-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
