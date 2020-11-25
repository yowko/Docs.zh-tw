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
ms.openlocfilehash: 0611b82e22ec9d5d2cde2a7f46e65b5e25733610
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731354"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="e78f1-102">IHostMemoryManager::GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="e78f1-102">IHostMemoryManager::GetMemoryLoad Method</span></span>

<span data-ttu-id="e78f1-103">取得目前使用中的實體記憶體數量，因此無法使用，如主機所報告。</span><span class="sxs-lookup"><span data-stu-id="e78f1-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="e78f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e78f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="e78f1-105">Parameters</span></span>  

 `pMemoryLoad`  
 <span data-ttu-id="e78f1-106">擴展目前使用中總實體記憶體的大約百分比指標。</span><span class="sxs-lookup"><span data-stu-id="e78f1-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="e78f1-107">擴展Common language runtime (CLR) 可用的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="e78f1-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e78f1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="e78f1-108">Return Value</span></span>  
  
|<span data-ttu-id="e78f1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e78f1-109">HRESULT</span></span>|<span data-ttu-id="e78f1-110">描述</span><span class="sxs-lookup"><span data-stu-id="e78f1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e78f1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e78f1-111">S_OK</span></span>|<span data-ttu-id="e78f1-112">`GetMemoryLoad` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="e78f1-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="e78f1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e78f1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e78f1-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e78f1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e78f1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e78f1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e78f1-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="e78f1-116">The call timed out.</span></span>|  
|<span data-ttu-id="e78f1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e78f1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e78f1-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e78f1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e78f1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e78f1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e78f1-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="e78f1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e78f1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e78f1-121">E_FAIL</span></span>|<span data-ttu-id="e78f1-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e78f1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e78f1-123">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="e78f1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e78f1-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e78f1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e78f1-125">備註</span><span class="sxs-lookup"><span data-stu-id="e78f1-125">Remarks</span></span>  

 <span data-ttu-id="e78f1-126">`GetMemoryLoad` 包裝 Win32 `GlobalMemoryStatus` 函數。</span><span class="sxs-lookup"><span data-stu-id="e78f1-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="e78f1-127">的值相當於所 `pMemoryLoad` `dwMemoryLoad` 傳回之結構中的欄位 `MEMORYSTATUS` `GlobalMemoryStatus` 。</span><span class="sxs-lookup"><span data-stu-id="e78f1-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="e78f1-128">執行時間會使用傳回值做為垃圾收集行程的啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="e78f1-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="e78f1-129">例如，如果主機報告大部分的記憶體正在使用中，垃圾收集行程可能會選擇從多個層代收集，以增加可能會變成可用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="e78f1-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78f1-130">需求</span><span class="sxs-lookup"><span data-stu-id="e78f1-130">Requirements</span></span>  

 <span data-ttu-id="e78f1-131">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e78f1-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e78f1-132">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e78f1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e78f1-133">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e78f1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e78f1-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e78f1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78f1-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e78f1-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="e78f1-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="e78f1-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
