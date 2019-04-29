---
title: IHostMemoryManager::GetMemoryLoad 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c43fd1c63b14fc3254044247213bf09453da870e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599373"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="152de-102">IHostMemoryManager::GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="152de-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="152de-103">取得目前為使用中，因此無法使用，與主應用程式所報告的實體記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="152de-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="152de-104">語法</span><span class="sxs-lookup"><span data-stu-id="152de-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="152de-105">參數</span><span class="sxs-lookup"><span data-stu-id="152de-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="152de-106">[out]目前正在使用的總實體記憶體的近似百分比指標。</span><span class="sxs-lookup"><span data-stu-id="152de-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="152de-107">[out]Common language runtime (CLR) 可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="152de-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="152de-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="152de-108">Return Value</span></span>  
  
|<span data-ttu-id="152de-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="152de-109">HRESULT</span></span>|<span data-ttu-id="152de-110">描述</span><span class="sxs-lookup"><span data-stu-id="152de-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="152de-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="152de-111">S_OK</span></span>|<span data-ttu-id="152de-112">`GetMemoryLoad` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="152de-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="152de-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="152de-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="152de-114">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="152de-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="152de-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="152de-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="152de-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="152de-116">The call timed out.</span></span>|  
|<span data-ttu-id="152de-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="152de-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="152de-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="152de-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="152de-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="152de-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="152de-120">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="152de-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="152de-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="152de-121">E_FAIL</span></span>|<span data-ttu-id="152de-122">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="152de-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="152de-123">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="152de-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="152de-124">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="152de-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="152de-125">備註</span><span class="sxs-lookup"><span data-stu-id="152de-125">Remarks</span></span>  
 <span data-ttu-id="152de-126">`GetMemoryLoad` 包裝 Win32`GlobalMemoryStatus`函式。</span><span class="sxs-lookup"><span data-stu-id="152de-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="152de-127">值`pMemoryLoad`相當於`dwMemoryLoad`欄位中`MEMORYSTATUS`所傳回的結構`GlobalMemoryStatus`。</span><span class="sxs-lookup"><span data-stu-id="152de-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="152de-128">執行階段會使用啟發學習法為傳回值，記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="152de-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="152de-129">比方說，如果主應用程式會報告使用中大部分的記憶體，記憶體回收行程可能會選擇收集來自多個層代增加可能變成可用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="152de-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152de-130">需求</span><span class="sxs-lookup"><span data-stu-id="152de-130">Requirements</span></span>  
 <span data-ttu-id="152de-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="152de-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152de-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="152de-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="152de-133">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="152de-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="152de-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152de-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152de-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="152de-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="152de-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="152de-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
