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
ms.openlocfilehash: 05df50d80c6b8962b3bdfe2708d5f9d30c58aaea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723918"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="77865-102">ICorConfiguration::SetDebuggerThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="77865-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="77865-103">設定偵錯工具將呼叫的回呼介面，作為 common language runtime (CLR) 執行緒遭到封鎖和解除封鎖以進行調試。</span><span class="sxs-lookup"><span data-stu-id="77865-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77865-104">語法</span><span class="sxs-lookup"><span data-stu-id="77865-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77865-105">參數</span><span class="sxs-lookup"><span data-stu-id="77865-105">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="77865-106">在 [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) 物件的指標，該物件會通知主機有關偵錯工具的執行緒封鎖和解除封鎖。</span><span class="sxs-lookup"><span data-stu-id="77865-106">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77865-107">需求</span><span class="sxs-lookup"><span data-stu-id="77865-107">Requirements</span></span>  

 <span data-ttu-id="77865-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77865-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77865-109">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="77865-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77865-110">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="77865-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77865-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77865-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77865-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77865-112">See also</span></span>

- [<span data-ttu-id="77865-113">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="77865-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
