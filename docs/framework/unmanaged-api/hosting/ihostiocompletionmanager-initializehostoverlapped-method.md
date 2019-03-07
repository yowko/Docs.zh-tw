---
title: IHostIoCompletionManager::InitializeHostOverlapped 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d2959a27bb848d05dc44492152866b2d535b68
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503160"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="5d3ab-102">IHostIoCompletionManager::InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="5d3ab-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="5d3ab-103">主應用程式提供有機會初始化任何自訂的資料，要附加至 Win32`OVERLAPPED`非同步的 I/O 要求所使用的結構。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d3ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d3ab-104">Syntax</span></span>  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d3ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d3ab-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="5d3ab-106">[in]Win32 指標`OVERLAPPED`結構以包含在 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d3ab-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d3ab-107">Return Value</span></span>  
  
|<span data-ttu-id="5d3ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d3ab-108">HRESULT</span></span>|<span data-ttu-id="5d3ab-109">描述</span><span class="sxs-lookup"><span data-stu-id="5d3ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d3ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d3ab-110">S_OK</span></span>|<span data-ttu-id="5d3ab-111">`InitializeHostOverlapped` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="5d3ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d3ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d3ab-113">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d3ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d3ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d3ab-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="5d3ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d3ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d3ab-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d3ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d3ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d3ab-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d3ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d3ab-120">E_FAIL</span></span>|<span data-ttu-id="5d3ab-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d3ab-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d3ab-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5d3ab-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5d3ab-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5d3ab-125">記憶體不足，無法配置所要求的資源。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d3ab-126">備註</span><span class="sxs-lookup"><span data-stu-id="5d3ab-126">Remarks</span></span>  
 <span data-ttu-id="5d3ab-127">Windows 平台函式會使用`OVERLAPPED`非同步 I/O 要求的狀態儲存的結構。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="5d3ab-128">CLR 會呼叫`InitializeHostOverlapped`方法，讓主應用程式来新增自訂資料的機會`OVERLAPPED`執行個體。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5d3ab-129">若要取得其自訂資料區塊的開頭，主機必須的大小設定位移`OVERLAPPED`結構 (`sizeof(OVERLAPPED)`)。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="5d3ab-130">傳回值 E_OUTOFMEMORY 表示主機已無法初始化其自訂的資料。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="5d3ab-131">在此情況下，CLR 會回報錯誤，並使呼叫失敗。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d3ab-132">需求</span><span class="sxs-lookup"><span data-stu-id="5d3ab-132">Requirements</span></span>  
 <span data-ttu-id="5d3ab-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3ab-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d3ab-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d3ab-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d3ab-135">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5d3ab-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d3ab-136">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d3ab-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d3ab-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d3ab-137">See also</span></span>
- [<span data-ttu-id="5d3ab-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d3ab-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5d3ab-139">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="5d3ab-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="5d3ab-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d3ab-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
