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
ms.openlocfilehash: 47ff178cc9ab798593848e56fc7bba8ac82ae295
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154228"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="62d68-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="62d68-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="62d68-103">通知主機有關的傳送此回呼的執行緒偵錯服務內的區塊。</span><span class="sxs-lookup"><span data-stu-id="62d68-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d68-104">語法</span><span class="sxs-lookup"><span data-stu-id="62d68-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="62d68-105">備註</span><span class="sxs-lookup"><span data-stu-id="62d68-105">Remarks</span></span>  
 <span data-ttu-id="62d68-106">`ThreadIsBlockingForDebugger`一律會在執行階段的執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="62d68-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="62d68-107">`ThreadIsBlockingForDebugger`方法可讓主應用程式執行時則執行緒會封鎖另一個動作的機會。</span><span class="sxs-lookup"><span data-stu-id="62d68-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d68-108">需求</span><span class="sxs-lookup"><span data-stu-id="62d68-108">Requirements</span></span>  
 <span data-ttu-id="62d68-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62d68-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d68-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62d68-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62d68-111">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="62d68-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="62d68-112">NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="62d68-112">NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62d68-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62d68-113">See also</span></span>

- [<span data-ttu-id="62d68-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="62d68-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
