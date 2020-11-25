---
title: IHostTask::Start 方法
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: 4143c3d25dd5262a10b53708a249910cc79f5314
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720434"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="db5a4-102">IHostTask::Start 方法</span><span class="sxs-lookup"><span data-stu-id="db5a4-102">IHostTask::Start Method</span></span>

<span data-ttu-id="db5a4-103">要求主機將目前 [IHostTask](ihosttask-interface.md) 實例所代表的工作從暫止狀態移至即時狀態，其中可以執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="db5a4-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db5a4-104">語法</span><span class="sxs-lookup"><span data-stu-id="db5a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="db5a4-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="db5a4-105">Return Value</span></span>  
  
|<span data-ttu-id="db5a4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="db5a4-106">HRESULT</span></span>|<span data-ttu-id="db5a4-107">描述</span><span class="sxs-lookup"><span data-stu-id="db5a4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="db5a4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="db5a4-108">S_OK</span></span>|<span data-ttu-id="db5a4-109">已成功地開始傳回。</span><span class="sxs-lookup"><span data-stu-id="db5a4-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="db5a4-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="db5a4-110">E_FAIL</span></span>|<span data-ttu-id="db5a4-111">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="db5a4-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="db5a4-112">當方法傳回 E_FAIL 時，common language runtime (CLR) 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="db5a4-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="db5a4-113">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="db5a4-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db5a4-114">備註</span><span class="sxs-lookup"><span data-stu-id="db5a4-114">Remarks</span></span>  

 <span data-ttu-id="db5a4-115">`Start` 一律會傳回 S_OK 的 HRESULT 值，但發生嚴重失敗的情況除外。</span><span class="sxs-lookup"><span data-stu-id="db5a4-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db5a4-116">需求</span><span class="sxs-lookup"><span data-stu-id="db5a4-116">Requirements</span></span>  

 <span data-ttu-id="db5a4-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db5a4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db5a4-118">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="db5a4-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db5a4-119">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="db5a4-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db5a4-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db5a4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db5a4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5a4-121">See also</span></span>

- [<span data-ttu-id="db5a4-122">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="db5a4-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="db5a4-123">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="db5a4-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="db5a4-124">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="db5a4-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="db5a4-125">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="db5a4-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
