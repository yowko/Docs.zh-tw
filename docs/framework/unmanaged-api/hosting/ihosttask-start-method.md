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
ms.openlocfilehash: fe93a3bab267ccca941974b734c86329ad0f4d03
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121342"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="fdbbd-102">IHostTask::Start 方法</span><span class="sxs-lookup"><span data-stu-id="fdbbd-102">IHostTask::Start Method</span></span>
<span data-ttu-id="fdbbd-103">要求主機將目前[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)實例所代表的工作從暫止狀態移動到即時狀態，讓程式碼可以在其中執行。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdbbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="fdbbd-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fdbbd-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="fdbbd-105">Return Value</span></span>  
  
|<span data-ttu-id="fdbbd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdbbd-106">HRESULT</span></span>|<span data-ttu-id="fdbbd-107">描述</span><span class="sxs-lookup"><span data-stu-id="fdbbd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdbbd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdbbd-108">S_OK</span></span>|<span data-ttu-id="fdbbd-109">成功地啟動傳回。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="fdbbd-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdbbd-110">E_FAIL</span></span>|<span data-ttu-id="fdbbd-111">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdbbd-112">當方法傳回 E_FAIL 時，common language runtime （CLR）在進程內就無法再使用。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="fdbbd-113">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdbbd-114">備註</span><span class="sxs-lookup"><span data-stu-id="fdbbd-114">Remarks</span></span>  
 <span data-ttu-id="fdbbd-115">`Start` 一律會傳回 S_OK 的 HRESULT 值，但發生嚴重失敗的情況除外。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdbbd-116">需求</span><span class="sxs-lookup"><span data-stu-id="fdbbd-116">Requirements</span></span>  
 <span data-ttu-id="fdbbd-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fdbbd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdbbd-118">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="fdbbd-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdbbd-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fdbbd-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdbbd-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdbbd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdbbd-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="fdbbd-121">See also</span></span>

- [<span data-ttu-id="fdbbd-122">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="fdbbd-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fdbbd-123">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fdbbd-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fdbbd-124">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="fdbbd-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fdbbd-125">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="fdbbd-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
