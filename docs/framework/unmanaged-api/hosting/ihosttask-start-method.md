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
ms.openlocfilehash: a4e8211f091b2a3a4f24d8350f6d7dbe7d7920af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842383"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="8cfcb-102">IHostTask::Start 方法</span><span class="sxs-lookup"><span data-stu-id="8cfcb-102">IHostTask::Start Method</span></span>
<span data-ttu-id="8cfcb-103">要求主機將目前[IHostTask](ihosttask-interface.md)實例所代表的工作從暫止狀態移動到即時狀態，讓程式碼可以在其中執行。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cfcb-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cfcb-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8cfcb-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="8cfcb-105">Return Value</span></span>  
  
|<span data-ttu-id="8cfcb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cfcb-106">HRESULT</span></span>|<span data-ttu-id="8cfcb-107">描述</span><span class="sxs-lookup"><span data-stu-id="8cfcb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8cfcb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="8cfcb-108">S_OK</span></span>|<span data-ttu-id="8cfcb-109">成功地啟動傳回。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="8cfcb-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8cfcb-110">E_FAIL</span></span>|<span data-ttu-id="8cfcb-111">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8cfcb-112">當方法傳回 E_FAIL 時，common language runtime （CLR）在進程內就無法再使用。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="8cfcb-113">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cfcb-114">備註</span><span class="sxs-lookup"><span data-stu-id="8cfcb-114">Remarks</span></span>  
 <span data-ttu-id="8cfcb-115">`Start`一律會傳回 S_OK 的 HRESULT 值，但發生嚴重失敗的情況除外。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cfcb-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="8cfcb-116">Requirements</span></span>  
 <span data-ttu-id="8cfcb-117">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cfcb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cfcb-118">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="8cfcb-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8cfcb-119">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8cfcb-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cfcb-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cfcb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfcb-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cfcb-121">See also</span></span>

- [<span data-ttu-id="8cfcb-122">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="8cfcb-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8cfcb-123">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8cfcb-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8cfcb-124">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="8cfcb-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8cfcb-125">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="8cfcb-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
