---
title: "IHostIoCompletionManager::GetHostOverlappedSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 41fc1a4a0debe0c302115c79962c0da50cc4ee37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="7c403-102">IHostIoCompletionManager::GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="7c403-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>
<span data-ttu-id="7c403-103">取得主應用程式想要附加至 I/O 要求的任何自訂資料的大小。</span><span class="sxs-lookup"><span data-stu-id="7c403-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c403-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c403-104">Syntax</span></span>  
  
```  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c403-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c403-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="7c403-106">[out]除了 Win32 的大小，應該配置 common language runtime (CLR) 的位元組數目的指標`OVERLAPPED`物件。</span><span class="sxs-lookup"><span data-stu-id="7c403-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c403-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="7c403-107">Return Value</span></span>  
  
|<span data-ttu-id="7c403-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c403-108">HRESULT</span></span>|<span data-ttu-id="7c403-109">描述</span><span class="sxs-lookup"><span data-stu-id="7c403-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c403-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c403-110">S_OK</span></span>|<span data-ttu-id="7c403-111">`GetHostOverlappedSize`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="7c403-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="7c403-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c403-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c403-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="7c403-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c403-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c403-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c403-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="7c403-115">The call timed out.</span></span>|  
|<span data-ttu-id="7c403-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c403-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c403-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="7c403-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c403-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c403-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c403-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="7c403-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c403-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c403-120">E_FAIL</span></span>|<span data-ttu-id="7c403-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="7c403-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c403-122">方法會傳回 E_FAIL CLR 已不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="7c403-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c403-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="7c403-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c403-124">備註</span><span class="sxs-lookup"><span data-stu-id="7c403-124">Remarks</span></span>  
 <span data-ttu-id="7c403-125">所有 Windows 平台 api 的非同步 I/O 呼叫都採用 Win32`OVERLAPPED`物件，提供資訊，例如檔案指標的位置。</span><span class="sxs-lookup"><span data-stu-id="7c403-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="7c403-126">若要維護狀態，通常進行非同步的 I/O 呼叫的應用程式加入自訂資料結構。</span><span class="sxs-lookup"><span data-stu-id="7c403-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="7c403-127">`GetHostOverlappedSize`和[ihostiocompletionmanager:: Initializehostoverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)提供一個機會，供主機用來包含這類自訂的資料。</span><span class="sxs-lookup"><span data-stu-id="7c403-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="7c403-128">CLR 會呼叫`GetHostOverlappedSize`方法來判斷自訂主應用程式想要附加至的資料大小`OVERLAPPED`物件。</span><span class="sxs-lookup"><span data-stu-id="7c403-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c403-129">`GetHostOverlappedSize`是只呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="7c403-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="7c403-130">主機的自訂資料必須是相同大小的每個 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="7c403-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7c403-131">大小`OVERLAPPED`物件本身未包含的值在`pcbSize`。</span><span class="sxs-lookup"><span data-stu-id="7c403-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="7c403-132">如需有關`OVERLAPPED`結構時，請參閱 Windows 平台。</span><span class="sxs-lookup"><span data-stu-id="7c403-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c403-133">需求</span><span class="sxs-lookup"><span data-stu-id="7c403-133">Requirements</span></span>  
 <span data-ttu-id="7c403-134">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c403-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c403-135">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c403-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c403-136">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7c403-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c403-137">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c403-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c403-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="7c403-138">See Also</span></span>  
 <xref:System.Threading.NativeOverlapped>  
 [<span data-ttu-id="7c403-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7c403-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="7c403-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="7c403-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
