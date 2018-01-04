---
title: "IHostMemoryManager::GetMemoryLoad 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.GetMemoryLoad
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 320881447eed00bf0dfeada0f5fbd224c32dfe96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="24062-102">IHostMemoryManager::GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="24062-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="24062-103">取得目前在使用中，且因此無法使用，與主應用程式所報告的實體記憶體量。</span><span class="sxs-lookup"><span data-stu-id="24062-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24062-104">語法</span><span class="sxs-lookup"><span data-stu-id="24062-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24062-105">參數</span><span class="sxs-lookup"><span data-stu-id="24062-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="24062-106">[out]目前正在使用的總實體記憶體的近似百分比指標。</span><span class="sxs-lookup"><span data-stu-id="24062-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="24062-107">[out]Common language runtime (CLR) 可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="24062-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24062-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="24062-108">Return Value</span></span>  
  
|<span data-ttu-id="24062-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24062-109">HRESULT</span></span>|<span data-ttu-id="24062-110">描述</span><span class="sxs-lookup"><span data-stu-id="24062-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24062-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="24062-111">S_OK</span></span>|<span data-ttu-id="24062-112">`GetMemoryLoad`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="24062-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="24062-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24062-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24062-114">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="24062-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24062-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24062-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24062-116">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="24062-116">The call timed out.</span></span>|  
|<span data-ttu-id="24062-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24062-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24062-118">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="24062-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24062-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24062-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24062-120">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="24062-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24062-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24062-121">E_FAIL</span></span>|<span data-ttu-id="24062-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="24062-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24062-123">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="24062-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24062-124">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="24062-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24062-125">備註</span><span class="sxs-lookup"><span data-stu-id="24062-125">Remarks</span></span>  
 <span data-ttu-id="24062-126">`GetMemoryLoad`包裝 Win32`GlobalMemoryStatus`函式。</span><span class="sxs-lookup"><span data-stu-id="24062-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="24062-127">值`pMemoryLoad`就相當於`dwMemoryLoad`欄位`MEMORYSTATUS`從傳回的結構`GlobalMemoryStatus`。</span><span class="sxs-lookup"><span data-stu-id="24062-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="24062-128">Runtime 會使用啟發學習法為傳回值，記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="24062-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="24062-129">比方說，如果主應用程式會報告使用中大部分的記憶體，記憶體回收行程可能會選擇收集多個層代增加可能變成可用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="24062-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24062-130">需求</span><span class="sxs-lookup"><span data-stu-id="24062-130">Requirements</span></span>  
 <span data-ttu-id="24062-131">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24062-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24062-132">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24062-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24062-133">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="24062-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24062-134">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24062-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24062-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="24062-135">See Also</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
 [<span data-ttu-id="24062-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="24062-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
