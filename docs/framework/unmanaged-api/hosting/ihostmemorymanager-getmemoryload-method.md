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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176275"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="81e38-102">IHostMemoryManager::GetMemoryLoad 方法</span><span class="sxs-lookup"><span data-stu-id="81e38-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="81e38-103">獲取主機報告當前正在使用且因此不可用的實體記憶體量。</span><span class="sxs-lookup"><span data-stu-id="81e38-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e38-104">語法</span><span class="sxs-lookup"><span data-stu-id="81e38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81e38-105">參數</span><span class="sxs-lookup"><span data-stu-id="81e38-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="81e38-106">[出]指向當前正在使用的總實體記憶體的近似百分比的指標。</span><span class="sxs-lookup"><span data-stu-id="81e38-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="81e38-107">[出]指向公共語言運行時 （CLR） 可用的位元組數的指標。</span><span class="sxs-lookup"><span data-stu-id="81e38-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e38-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="81e38-108">Return Value</span></span>  
  
|<span data-ttu-id="81e38-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81e38-109">HRESULT</span></span>|<span data-ttu-id="81e38-110">描述</span><span class="sxs-lookup"><span data-stu-id="81e38-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81e38-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="81e38-111">S_OK</span></span>|<span data-ttu-id="81e38-112">`GetMemoryLoad`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="81e38-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="81e38-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81e38-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81e38-114">CLR 尚未載入到進程中，或者 CLR 處於無法成功運行託管代碼或成功處理調用的狀態。</span><span class="sxs-lookup"><span data-stu-id="81e38-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81e38-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81e38-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81e38-116">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="81e38-116">The call timed out.</span></span>|  
|<span data-ttu-id="81e38-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81e38-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81e38-118">調用方不擁有鎖。</span><span class="sxs-lookup"><span data-stu-id="81e38-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81e38-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81e38-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81e38-120">當阻塞的執行緒或光纖等待事件時，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="81e38-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81e38-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81e38-121">E_FAIL</span></span>|<span data-ttu-id="81e38-122">發生了未知的災難性故障。</span><span class="sxs-lookup"><span data-stu-id="81e38-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81e38-123">當方法返回E_FAIL時，CLR 在進程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="81e38-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81e38-124">對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="81e38-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e38-125">備註</span><span class="sxs-lookup"><span data-stu-id="81e38-125">Remarks</span></span>  
 <span data-ttu-id="81e38-126">`GetMemoryLoad`包裝 Win32`GlobalMemoryStatus`函數。</span><span class="sxs-lookup"><span data-stu-id="81e38-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="81e38-127">的值`pMemoryLoad`相當於從`dwMemoryLoad``MEMORYSTATUS``GlobalMemoryStatus`返回的結構中的欄位。</span><span class="sxs-lookup"><span data-stu-id="81e38-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="81e38-128">運行時使用傳回值作為垃圾回收器的啟發式。</span><span class="sxs-lookup"><span data-stu-id="81e38-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="81e38-129">例如，如果主機報告大多數記憶體正在使用中，垃圾回收器可能會選擇從多代收集，以增加可能可用的記憶體量。</span><span class="sxs-lookup"><span data-stu-id="81e38-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e38-130">需求</span><span class="sxs-lookup"><span data-stu-id="81e38-130">Requirements</span></span>  
 <span data-ttu-id="81e38-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81e38-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e38-132">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81e38-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81e38-133">**庫：** 作為資源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="81e38-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81e38-134">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e38-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e38-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e38-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="81e38-136">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="81e38-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
