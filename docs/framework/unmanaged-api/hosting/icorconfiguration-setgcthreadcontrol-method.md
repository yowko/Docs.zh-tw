---
title: ICorConfiguration::SetGCThreadControl 方法
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
ms.openlocfilehash: 28b012bbe3f8c11ecd0afb8b5905336bd99c349c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724022"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="6d9d4-102">ICorConfiguration::SetGCThreadControl 方法</span><span class="sxs-lookup"><span data-stu-id="6d9d4-102">ICorConfiguration::SetGCThreadControl Method</span></span>

<span data-ttu-id="6d9d4-103">設定回呼介面，以排程非執行時間工作的執行緒，否則將會遭到封鎖，以進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="6d9d4-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6d9d4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d9d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="6d9d4-105">Parameters</span></span>  

 `pGCThreadControl`  
 <span data-ttu-id="6d9d4-106">在 [IGCThreadControl](igcthreadcontrol-interface.md) 物件的指標，該物件會通知主機有關非執行時間工作的執行緒擱置。</span><span class="sxs-lookup"><span data-stu-id="6d9d4-106">[in] A pointer to an [IGCThreadControl](igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d9d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="6d9d4-107">Remarks</span></span>  

 <span data-ttu-id="6d9d4-108">主機可以在 [IGCThreadControl：： ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) 回呼中選擇是否要重新排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="6d9d4-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d9d4-109">需求</span><span class="sxs-lookup"><span data-stu-id="6d9d4-109">Requirements</span></span>  

 <span data-ttu-id="6d9d4-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6d9d4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d9d4-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6d9d4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6d9d4-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6d9d4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6d9d4-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d9d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9d4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d9d4-114">See also</span></span>

- [<span data-ttu-id="6d9d4-115">ICorConfiguration 介面</span><span class="sxs-lookup"><span data-stu-id="6d9d4-115">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
