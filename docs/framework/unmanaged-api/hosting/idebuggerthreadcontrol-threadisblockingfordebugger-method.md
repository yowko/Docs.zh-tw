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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa72c136e98f80df6d2868c447e1c535ae61af06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739624"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="491dd-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="491dd-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="491dd-103">通知主機有關的傳送此回呼的執行緒偵錯服務內的區塊。</span><span class="sxs-lookup"><span data-stu-id="491dd-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491dd-104">語法</span><span class="sxs-lookup"><span data-stu-id="491dd-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="491dd-105">備註</span><span class="sxs-lookup"><span data-stu-id="491dd-105">Remarks</span></span>  
 <span data-ttu-id="491dd-106">`ThreadIsBlockingForDebugger`一律會在執行階段的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="491dd-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="491dd-107">`ThreadIsBlockingForDebugger`方法可讓主應用程式執行時則執行緒會封鎖另一個動作的機會。</span><span class="sxs-lookup"><span data-stu-id="491dd-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491dd-108">需求</span><span class="sxs-lookup"><span data-stu-id="491dd-108">Requirements</span></span>  
 <span data-ttu-id="491dd-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="491dd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491dd-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="491dd-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="491dd-111">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="491dd-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="491dd-112">**NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491dd-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491dd-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="491dd-113">See also</span></span>
- [<span data-ttu-id="491dd-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="491dd-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
