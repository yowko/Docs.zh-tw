---
title: IHostIoCompletionManager::GetHostOverlappedSize 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54e72205f8f976498df3b1fe1e055fb7df12d68e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780688"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="7862a-102">IHostIoCompletionManager::GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="7862a-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="7862a-103">取得主應用程式想要附加至 I/O 要求的任何自訂資料的大小。</span><span class="sxs-lookup"><span data-stu-id="7862a-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7862a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7862a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7862a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7862a-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="7862a-106">[out]除了 Win32 的大小應該配置的 common language runtime (CLR) 的位元組數目的指標`OVERLAPPED`物件。</span><span class="sxs-lookup"><span data-stu-id="7862a-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7862a-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7862a-107">Return Value</span></span>  
  
|<span data-ttu-id="7862a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7862a-108">HRESULT</span></span>|<span data-ttu-id="7862a-109">說明</span><span class="sxs-lookup"><span data-stu-id="7862a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7862a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7862a-110">S_OK</span></span>|<span data-ttu-id="7862a-111">`GetHostOverlappedSize` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7862a-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="7862a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7862a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7862a-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="7862a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7862a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7862a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7862a-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="7862a-115">The call timed out.</span></span>|  
|<span data-ttu-id="7862a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7862a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7862a-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7862a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7862a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7862a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7862a-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="7862a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7862a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7862a-120">E_FAIL</span></span>|<span data-ttu-id="7862a-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="7862a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7862a-122">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="7862a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7862a-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7862a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7862a-124">備註</span><span class="sxs-lookup"><span data-stu-id="7862a-124">Remarks</span></span>  
 <span data-ttu-id="7862a-125">所有 Windows 平台 api 的非同步 I/O 呼叫都採用 Win32`OVERLAPPED`物件，提供資訊，例如檔案指標位置。</span><span class="sxs-lookup"><span data-stu-id="7862a-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="7862a-126">若要維護狀態，通常是進行非同步的 I/O 呼叫的應用程式會將自訂資料新增至結構。</span><span class="sxs-lookup"><span data-stu-id="7862a-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="7862a-127">`GetHostOverlappedSize` 並[ihostiocompletionmanager:: Initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)讓主應用程式包含這類自訂資料的機會。</span><span class="sxs-lookup"><span data-stu-id="7862a-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="7862a-128">CLR 會呼叫`GetHostOverlappedSize`方法，以判斷主機想要附加至自訂資料的大小`OVERLAPPED`物件。</span><span class="sxs-lookup"><span data-stu-id="7862a-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7862a-129">`GetHostOverlappedSize` 是只呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="7862a-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="7862a-130">主機的自訂資料必須是相同的大小，為每個 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="7862a-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7862a-131">大小`OVERLAPPED`的值中不包含物件本身`pcbSize`。</span><span class="sxs-lookup"><span data-stu-id="7862a-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="7862a-132">如需詳細資訊`OVERLAPPED`結構，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="7862a-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7862a-133">需求</span><span class="sxs-lookup"><span data-stu-id="7862a-133">Requirements</span></span>  
 <span data-ttu-id="7862a-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7862a-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7862a-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7862a-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7862a-136">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7862a-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7862a-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7862a-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7862a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7862a-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="7862a-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7862a-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7862a-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7862a-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
