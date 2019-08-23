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
ms.openlocfilehash: ac7014962b99ac167e8192c13b2bae5ca92470f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948518"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="eaa8f-102">IHostIoCompletionManager::InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="eaa8f-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="eaa8f-103">讓主機有機會初始化任何自訂資料, 以附加至用於非同步 i/o `OVERLAPPED`要求的 Win32 結構。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaa8f-104">語法</span><span class="sxs-lookup"><span data-stu-id="eaa8f-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eaa8f-105">參數</span><span class="sxs-lookup"><span data-stu-id="eaa8f-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="eaa8f-106">在要包含在 i/o 要求`OVERLAPPED`中的 Win32 結構指標。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eaa8f-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="eaa8f-107">Return Value</span></span>  
  
|<span data-ttu-id="eaa8f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eaa8f-108">HRESULT</span></span>|<span data-ttu-id="eaa8f-109">描述</span><span class="sxs-lookup"><span data-stu-id="eaa8f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eaa8f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eaa8f-110">S_OK</span></span>|<span data-ttu-id="eaa8f-111">`InitializeHostOverlapped`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="eaa8f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eaa8f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eaa8f-113">Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eaa8f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eaa8f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eaa8f-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-115">The call timed out.</span></span>|  
|<span data-ttu-id="eaa8f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eaa8f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eaa8f-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eaa8f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eaa8f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eaa8f-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eaa8f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eaa8f-120">E_FAIL</span></span>|<span data-ttu-id="eaa8f-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eaa8f-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eaa8f-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="eaa8f-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="eaa8f-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="eaa8f-125">沒有足夠的記憶體可用來配置要求的資源。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eaa8f-126">備註</span><span class="sxs-lookup"><span data-stu-id="eaa8f-126">Remarks</span></span>  
 <span data-ttu-id="eaa8f-127">Windows 平臺函式會使用`OVERLAPPED`結構來儲存非同步 i/o 要求的狀態。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="eaa8f-128">CLR 會呼叫`InitializeHostOverlapped`方法, 讓主機有`OVERLAPPED`機會將自訂資料附加至實例。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eaa8f-129">若要取得自訂資料區塊的開頭, 主機必須將位移設定為`OVERLAPPED`結構的大小 (`sizeof(OVERLAPPED)`)。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="eaa8f-130">E_OUTOFMEMORY 的傳回值表示主機無法初始化其自訂資料。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="eaa8f-131">在此情況下, CLR 會報告錯誤, 並導致呼叫失敗。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eaa8f-132">需求</span><span class="sxs-lookup"><span data-stu-id="eaa8f-132">Requirements</span></span>  
 <span data-ttu-id="eaa8f-133">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eaa8f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eaa8f-134">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eaa8f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eaa8f-135">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="eaa8f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eaa8f-136">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eaa8f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaa8f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eaa8f-137">See also</span></span>

- [<span data-ttu-id="eaa8f-138">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eaa8f-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="eaa8f-139">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="eaa8f-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="eaa8f-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="eaa8f-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
