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
ms.openlocfilehash: c43f906961b9e76d5f0f34ba5a5b2f656f5b1488
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937511"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="5d927-102">IHostIoCompletionManager::GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="5d927-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="5d927-103">取得主機打算附加到 i/o 要求的任何自訂資料大小。</span><span class="sxs-lookup"><span data-stu-id="5d927-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d927-104">語法</span><span class="sxs-lookup"><span data-stu-id="5d927-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d927-105">參數</span><span class="sxs-lookup"><span data-stu-id="5d927-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="5d927-106">脫銷除了 Win32 `OVERLAPPED`物件的大小以外, common language runtime (CLR) 應配置的位元組數目指標。</span><span class="sxs-lookup"><span data-stu-id="5d927-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d927-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="5d927-107">Return Value</span></span>  
  
|<span data-ttu-id="5d927-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d927-108">HRESULT</span></span>|<span data-ttu-id="5d927-109">說明</span><span class="sxs-lookup"><span data-stu-id="5d927-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d927-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5d927-110">S_OK</span></span>|<span data-ttu-id="5d927-111">`GetHostOverlappedSize`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5d927-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="5d927-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5d927-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5d927-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="5d927-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5d927-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5d927-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5d927-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="5d927-115">The call timed out.</span></span>|  
|<span data-ttu-id="5d927-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5d927-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5d927-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="5d927-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5d927-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5d927-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5d927-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="5d927-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5d927-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5d927-120">E_FAIL</span></span>|<span data-ttu-id="5d927-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="5d927-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5d927-122">當方法傳回 E_FAIL 時, CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="5d927-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5d927-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="5d927-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d927-124">備註</span><span class="sxs-lookup"><span data-stu-id="5d927-124">Remarks</span></span>  
 <span data-ttu-id="5d927-125">所有對 Windows 平臺 api 的非同步 i/o 呼叫都會接受一個 Win32 `OVERLAPPED`物件, 它會提供檔案指標位置等資訊。</span><span class="sxs-lookup"><span data-stu-id="5d927-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="5d927-126">若要維持狀態, 進行非同步 i/o 呼叫的應用程式通常會將自訂資料加入至結構。</span><span class="sxs-lookup"><span data-stu-id="5d927-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="5d927-127">`GetHostOverlappedSize`和[IHostIoCompletionManager:: InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)提供機會讓主機加入這類自訂資料。</span><span class="sxs-lookup"><span data-stu-id="5d927-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="5d927-128">CLR 會呼叫`GetHostOverlappedSize`方法, 以判斷主機想要附加`OVERLAPPED`至物件的自訂資料大小。</span><span class="sxs-lookup"><span data-stu-id="5d927-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d927-129">`GetHostOverlappedSize`只會呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="5d927-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="5d927-130">主機的自訂資料必須與每個 i/o 要求的大小相同。</span><span class="sxs-lookup"><span data-stu-id="5d927-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d927-131">`OVERLAPPED`物件本身的大小不會包含在的`pcbSize`值中。</span><span class="sxs-lookup"><span data-stu-id="5d927-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="5d927-132">如需`OVERLAPPED`結構的詳細資訊, 請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="5d927-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d927-133">需求</span><span class="sxs-lookup"><span data-stu-id="5d927-133">Requirements</span></span>  
 <span data-ttu-id="5d927-134">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d927-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d927-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5d927-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5d927-136">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5d927-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5d927-137">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d927-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d927-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d927-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="5d927-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d927-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="5d927-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="5d927-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
