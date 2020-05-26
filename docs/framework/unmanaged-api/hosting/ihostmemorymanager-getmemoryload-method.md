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
ms.openlocfilehash: 73d9ae865b2c971a4defcacf5bd6505836c74e02
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804498"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="80d31-102">IHostMemoryManager::GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="80d31-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="80d31-103">取得目前使用中的實體記憶體數量，因此無法供主機報告。</span><span class="sxs-lookup"><span data-stu-id="80d31-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d31-104">語法</span><span class="sxs-lookup"><span data-stu-id="80d31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80d31-105">參數</span><span class="sxs-lookup"><span data-stu-id="80d31-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="80d31-106">脫銷目前使用中實體記憶體總計的大約百分比指標。</span><span class="sxs-lookup"><span data-stu-id="80d31-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="80d31-107">脫銷通用語言執行時間（CLR）可用位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="80d31-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80d31-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="80d31-108">Return Value</span></span>  
  
|<span data-ttu-id="80d31-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80d31-109">HRESULT</span></span>|<span data-ttu-id="80d31-110">描述</span><span class="sxs-lookup"><span data-stu-id="80d31-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="80d31-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="80d31-111">S_OK</span></span>|<span data-ttu-id="80d31-112">`GetMemoryLoad`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="80d31-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="80d31-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="80d31-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="80d31-114">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="80d31-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="80d31-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="80d31-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="80d31-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="80d31-116">The call timed out.</span></span>|  
|<span data-ttu-id="80d31-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="80d31-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="80d31-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="80d31-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="80d31-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="80d31-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="80d31-120">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="80d31-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="80d31-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="80d31-121">E_FAIL</span></span>|<span data-ttu-id="80d31-122">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="80d31-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="80d31-123">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="80d31-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="80d31-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="80d31-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80d31-125">備註</span><span class="sxs-lookup"><span data-stu-id="80d31-125">Remarks</span></span>  
 <span data-ttu-id="80d31-126">`GetMemoryLoad`包裝 Win32 `GlobalMemoryStatus` 函數。</span><span class="sxs-lookup"><span data-stu-id="80d31-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="80d31-127">的值 `pMemoryLoad` 相當於所 `dwMemoryLoad` 傳回之結構中的欄位 `MEMORYSTATUS` `GlobalMemoryStatus` 。</span><span class="sxs-lookup"><span data-stu-id="80d31-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="80d31-128">執行時間會使用傳回值做為垃圾收集行程的啟發學習法。</span><span class="sxs-lookup"><span data-stu-id="80d31-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="80d31-129">例如，如果主機報告大部分的記憶體正在使用中，垃圾收集行程可能會選擇從多個層代收集，以增加可能會變成可用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="80d31-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d31-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="80d31-130">Requirements</span></span>  
 <span data-ttu-id="80d31-131">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80d31-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d31-132">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="80d31-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80d31-133">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80d31-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80d31-134">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d31-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d31-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80d31-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="80d31-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="80d31-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
