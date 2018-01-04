---
title: "IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59a4c13e84414dcd10b217134334777a745431c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="a4ed6-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="a4ed6-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="a4ed6-103">通知會傳送此回呼執行緒相關的主機至偵錯服務內的區塊。</span><span class="sxs-lookup"><span data-stu-id="a4ed6-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4ed6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4ed6-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a4ed6-105">備註</span><span class="sxs-lookup"><span data-stu-id="a4ed6-105">Remarks</span></span>  
 <span data-ttu-id="a4ed6-106">`ThreadIsBlockingForDebugger`一律會在執行階段執行緒上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="a4ed6-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="a4ed6-107">`ThreadIsBlockingForDebugger`方法可讓主機得以執行其他動作，而則執行緒會封鎖。</span><span class="sxs-lookup"><span data-stu-id="a4ed6-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4ed6-108">需求</span><span class="sxs-lookup"><span data-stu-id="a4ed6-108">Requirements</span></span>  
 <span data-ttu-id="a4ed6-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4ed6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4ed6-110">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4ed6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4ed6-111">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a4ed6-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4ed6-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4ed6-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ed6-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="a4ed6-113">See Also</span></span>  
 [<span data-ttu-id="a4ed6-114">IDebuggerThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="a4ed6-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
