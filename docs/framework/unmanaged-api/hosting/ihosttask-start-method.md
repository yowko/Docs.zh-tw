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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d45c5b09358430535438734b38e5dce5d1bcdd3e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101623"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="75582-102">IHostTask::Start 方法</span><span class="sxs-lookup"><span data-stu-id="75582-102">IHostTask::Start Method</span></span>
<span data-ttu-id="75582-103">要求主機移到表示由目前的工作[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)執行個體處於可以執行程式碼的即時狀態從已暫停。</span><span class="sxs-lookup"><span data-stu-id="75582-103">Requests that the host move the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75582-104">語法</span><span class="sxs-lookup"><span data-stu-id="75582-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="75582-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="75582-105">Return Value</span></span>  
  
|<span data-ttu-id="75582-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="75582-106">HRESULT</span></span>|<span data-ttu-id="75582-107">描述</span><span class="sxs-lookup"><span data-stu-id="75582-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="75582-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="75582-108">S_OK</span></span>|<span data-ttu-id="75582-109">開始在成功傳回。</span><span class="sxs-lookup"><span data-stu-id="75582-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="75582-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="75582-110">E_FAIL</span></span>|<span data-ttu-id="75582-111">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="75582-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="75582-112">方法會傳回 E_FAIL common language runtime (CLR) 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="75582-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="75582-113">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="75582-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75582-114">備註</span><span class="sxs-lookup"><span data-stu-id="75582-114">Remarks</span></span>  
 <span data-ttu-id="75582-115">`Start` 在發生嚴重失敗的情況下，除了一律傳回 s_ok 時，HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="75582-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75582-116">需求</span><span class="sxs-lookup"><span data-stu-id="75582-116">Requirements</span></span>  
 <span data-ttu-id="75582-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75582-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75582-118">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="75582-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="75582-119">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="75582-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75582-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75582-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75582-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75582-121">See also</span></span>

- [<span data-ttu-id="75582-122">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="75582-122">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="75582-123">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="75582-123">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="75582-124">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="75582-124">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="75582-125">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="75582-125">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
