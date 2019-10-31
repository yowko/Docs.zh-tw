---
title: IGCThreadControl::ThreadIsBlockingForSuspension 方法
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134745"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="168a7-102">IGCThreadControl::ThreadIsBlockingForSuspension 方法</span><span class="sxs-lookup"><span data-stu-id="168a7-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="168a7-103">通知主機正在進行呼叫的執行緒即將封鎖，可能是因為垃圾收集或其他暫停。</span><span class="sxs-lookup"><span data-stu-id="168a7-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="168a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="168a7-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="168a7-105">備註</span><span class="sxs-lookup"><span data-stu-id="168a7-105">Remarks</span></span>  
 <span data-ttu-id="168a7-106">主機可以在 `ThreadIsBlockingForSuspension` 回呼中選擇是否要重新排定執行緒。</span><span class="sxs-lookup"><span data-stu-id="168a7-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="168a7-107">需求</span><span class="sxs-lookup"><span data-stu-id="168a7-107">Requirements</span></span>  
 <span data-ttu-id="168a7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="168a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="168a7-109">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="168a7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="168a7-110">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="168a7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="168a7-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="168a7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168a7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="168a7-112">See also</span></span>

- [<span data-ttu-id="168a7-113">IGCThreadControl 介面</span><span class="sxs-lookup"><span data-stu-id="168a7-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
