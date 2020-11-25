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
ms.openlocfilehash: 397dbbeb0b85cb549a8b5917f977ecb13b3d6539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720213"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="bd8a9-102">IHostIoCompletionManager::InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="bd8a9-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="bd8a9-103">提供主機有機會初始化任何自訂資料，以附加至 `OVERLAPPED` 用於非同步 i/o 要求的 Win32 結構。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd8a9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd8a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd8a9-105">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="bd8a9-106">在要 `OVERLAPPED` 包含在 i/o 要求中的 Win32 結構指標。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd8a9-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="bd8a9-107">Return Value</span></span>  
  
|<span data-ttu-id="bd8a9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd8a9-108">HRESULT</span></span>|<span data-ttu-id="bd8a9-109">描述</span><span class="sxs-lookup"><span data-stu-id="bd8a9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd8a9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd8a9-110">S_OK</span></span>|<span data-ttu-id="bd8a9-111">`InitializeHostOverlapped` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="bd8a9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd8a9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd8a9-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bd8a9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bd8a9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bd8a9-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-115">The call timed out.</span></span>|  
|<span data-ttu-id="bd8a9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bd8a9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bd8a9-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bd8a9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bd8a9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bd8a9-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bd8a9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd8a9-120">E_FAIL</span></span>|<span data-ttu-id="bd8a9-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bd8a9-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bd8a9-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bd8a9-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="bd8a9-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="bd8a9-125">可用的記憶體不足，無法配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8a9-126">備註</span><span class="sxs-lookup"><span data-stu-id="bd8a9-126">Remarks</span></span>  

 <span data-ttu-id="bd8a9-127">Windows 平臺函數會使用 `OVERLAPPED` 結構來儲存非同步 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="bd8a9-128">CLR 會呼叫 `InitializeHostOverlapped` 方法，讓主機有機會將自訂資料附加至 `OVERLAPPED` 實例。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bd8a9-129">若要取得自訂資料區塊的開頭，主機必須將 () 的結構大小位移設定為 `OVERLAPPED` `sizeof(OVERLAPPED)` 。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="bd8a9-130">E_OUTOFMEMORY 的傳回值指出主機無法初始化其自訂資料。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="bd8a9-131">在此情況下，CLR 會報告錯誤，並導致呼叫失敗。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8a9-132">需求</span><span class="sxs-lookup"><span data-stu-id="bd8a9-132">Requirements</span></span>  

 <span data-ttu-id="bd8a9-133">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd8a9-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd8a9-134">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bd8a9-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd8a9-135">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="bd8a9-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd8a9-136">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd8a9-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8a9-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd8a9-137">See also</span></span>

- [<span data-ttu-id="bd8a9-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="bd8a9-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="bd8a9-139">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="bd8a9-139">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="bd8a9-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="bd8a9-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
