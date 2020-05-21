---
title: ICLRTaskManager::SetLocale 方法
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 8f316d91aab4c3862a0ad45b41539a4b80791ab9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762785"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="c5658-102">ICLRTaskManager::SetLocale 方法</span><span class="sxs-lookup"><span data-stu-id="c5658-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="c5658-103">通知 common language runtime （CLR），主控制項已在目前執行的工作上修改地區設定識別碼（對應至地理文化特性和語言）的值。</span><span class="sxs-lookup"><span data-stu-id="c5658-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5658-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5658-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5658-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5658-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="c5658-106">在地區設定識別碼值，對應至新指派的地理文化特性和語言。</span><span class="sxs-lookup"><span data-stu-id="c5658-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5658-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5658-107">Return Value</span></span>  
  
|<span data-ttu-id="c5658-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5658-108">HRESULT</span></span>|<span data-ttu-id="c5658-109">Description</span><span class="sxs-lookup"><span data-stu-id="c5658-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5658-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5658-110">S_OK</span></span>|<span data-ttu-id="c5658-111">此方法已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c5658-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="c5658-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5658-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5658-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c5658-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5658-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5658-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5658-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="c5658-115">The call timed out.</span></span>|  
|<span data-ttu-id="c5658-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5658-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5658-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c5658-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5658-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5658-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5658-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="c5658-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5658-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5658-120">E_FAIL</span></span>|<span data-ttu-id="c5658-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c5658-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5658-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="c5658-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5658-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c5658-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5658-124">備註</span><span class="sxs-lookup"><span data-stu-id="c5658-124">Remarks</span></span>  
 <span data-ttu-id="c5658-125">`SetLocale`讓主機有機會執行可能對地區設定同步處理的任何機制。</span><span class="sxs-lookup"><span data-stu-id="c5658-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5658-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="c5658-126">Requirements</span></span>  
 <span data-ttu-id="c5658-127">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5658-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5658-128">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c5658-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5658-129">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c5658-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5658-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5658-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5658-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5658-131">See also</span></span>

- [<span data-ttu-id="c5658-132">ICLRTask 介面</span><span class="sxs-lookup"><span data-stu-id="c5658-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="c5658-133">ICLRTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c5658-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="c5658-134">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="c5658-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="c5658-135">IHostTaskManager 介面</span><span class="sxs-lookup"><span data-stu-id="c5658-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
