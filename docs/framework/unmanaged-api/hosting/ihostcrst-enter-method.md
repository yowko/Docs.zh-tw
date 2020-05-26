---
title: IHostCrst::Enter 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
ms.openlocfilehash: 79afaac4dce1c4baa9802d81af90c425f5de7a08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804912"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="770ea-102">IHostCrst::Enter 方法</span><span class="sxs-lookup"><span data-stu-id="770ea-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="770ea-103">輸入目前[IHostCrst](ihostcrst-interface.md)實例所代表的重要區段。</span><span class="sxs-lookup"><span data-stu-id="770ea-103">Enters the critical section that is represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="770ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="770ea-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="770ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="770ea-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="770ea-106">在其中一個[WAIT_OPTION](wait-option-enumeration.md)值，指出當作業封鎖時，主機應採取的動作。</span><span class="sxs-lookup"><span data-stu-id="770ea-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="770ea-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="770ea-107">Return Value</span></span>  
  
|<span data-ttu-id="770ea-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="770ea-108">HRESULT</span></span>|<span data-ttu-id="770ea-109">描述</span><span class="sxs-lookup"><span data-stu-id="770ea-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="770ea-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="770ea-110">S_OK</span></span>|<span data-ttu-id="770ea-111">`Enter`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="770ea-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="770ea-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="770ea-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="770ea-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="770ea-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="770ea-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="770ea-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="770ea-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="770ea-115">The call timed out.</span></span>|  
|<span data-ttu-id="770ea-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="770ea-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="770ea-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="770ea-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="770ea-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="770ea-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="770ea-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="770ea-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="770ea-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="770ea-120">E_FAIL</span></span>|<span data-ttu-id="770ea-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="770ea-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="770ea-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="770ea-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="770ea-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="770ea-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="770ea-124">備註</span><span class="sxs-lookup"><span data-stu-id="770ea-124">Remarks</span></span>  
 <span data-ttu-id="770ea-125">`Enter`鏡像 Win32 `EnterCriticalSection` 函數。</span><span class="sxs-lookup"><span data-stu-id="770ea-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="770ea-126">在輸入重要區段之前，這個方法不會傳回。</span><span class="sxs-lookup"><span data-stu-id="770ea-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="770ea-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="770ea-127">Requirements</span></span>  
 <span data-ttu-id="770ea-128">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="770ea-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="770ea-129">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="770ea-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="770ea-130">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="770ea-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="770ea-131">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="770ea-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="770ea-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="770ea-132">See also</span></span>

- [<span data-ttu-id="770ea-133">ICLRSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="770ea-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="770ea-134">IHostCrst 介面</span><span class="sxs-lookup"><span data-stu-id="770ea-134">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="770ea-135">IHostSyncManager 介面</span><span class="sxs-lookup"><span data-stu-id="770ea-135">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
