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
ms.openlocfilehash: 612a5f08982b1db5c940a7cca93166480b21e612
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724854"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a><span data-ttu-id="61005-102">IHostIoCompletionManager::GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="61005-102">IHostIoCompletionManager::GetHostOverlappedSize Method</span></span>

<span data-ttu-id="61005-103">取得主機打算附加至 i/o 要求的任何自訂資料大小。</span><span class="sxs-lookup"><span data-stu-id="61005-103">Gets the size of any custom data the host intends to append to I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61005-104">語法</span><span class="sxs-lookup"><span data-stu-id="61005-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61005-105">參數</span><span class="sxs-lookup"><span data-stu-id="61005-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="61005-106">擴展除了 Win32 物件的大小之外，common language runtime (CLR) 應配置的位元組數目指標 `OVERLAPPED` 。</span><span class="sxs-lookup"><span data-stu-id="61005-106">[out] A pointer to the number of bytes that the common language runtime (CLR) should allocate in addition to the size of the Win32 `OVERLAPPED` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61005-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="61005-107">Return Value</span></span>  
  
|<span data-ttu-id="61005-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61005-108">HRESULT</span></span>|<span data-ttu-id="61005-109">描述</span><span class="sxs-lookup"><span data-stu-id="61005-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61005-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="61005-110">S_OK</span></span>|<span data-ttu-id="61005-111">`GetHostOverlappedSize` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="61005-111">`GetHostOverlappedSize` returned successfully.</span></span>|  
|<span data-ttu-id="61005-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61005-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61005-113">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="61005-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61005-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61005-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61005-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="61005-115">The call timed out.</span></span>|  
|<span data-ttu-id="61005-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61005-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61005-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="61005-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61005-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61005-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61005-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="61005-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61005-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61005-120">E_FAIL</span></span>|<span data-ttu-id="61005-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="61005-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61005-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="61005-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61005-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="61005-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61005-124">備註</span><span class="sxs-lookup"><span data-stu-id="61005-124">Remarks</span></span>  

 <span data-ttu-id="61005-125">所有對 Windows 平臺 Api 的非同步 i/o 呼叫都採用 Win32 `OVERLAPPED` 物件，此物件會提供檔案指標位置之類的資訊。</span><span class="sxs-lookup"><span data-stu-id="61005-125">All asynchronous I/O calls to Windows Platform APIs take a Win32 `OVERLAPPED` object, which provides information such as the file pointer position.</span></span> <span data-ttu-id="61005-126">為了維護狀態，進行非同步 i/o 呼叫的應用程式通常會將自訂資料新增至結構。</span><span class="sxs-lookup"><span data-stu-id="61005-126">To maintain state, applications that make asynchronous I/O calls typically add custom data to the structure.</span></span> <span data-ttu-id="61005-127">`GetHostOverlappedSize` 和 [IHostIoCompletionManager：： InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) 提供機會讓主機包含這類自訂資料。</span><span class="sxs-lookup"><span data-stu-id="61005-127">`GetHostOverlappedSize` and [IHostIoCompletionManager::InitializeHostOverlapped](ihostiocompletionmanager-initializehostoverlapped-method.md) provide an opportunity for the host to include such custom data.</span></span>  
  
 <span data-ttu-id="61005-128">CLR `GetHostOverlappedSize` 會呼叫方法來判斷主機要附加至物件的自訂資料大小 `OVERLAPPED` 。</span><span class="sxs-lookup"><span data-stu-id="61005-128">The CLR calls the `GetHostOverlappedSize` method to determine the size of the custom data that the host intends to append to the `OVERLAPPED` object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61005-129">`GetHostOverlappedSize` 只呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="61005-129">`GetHostOverlappedSize` is called only once.</span></span> <span data-ttu-id="61005-130">主機的自訂資料必須是每個 i/o 要求的相同大小。</span><span class="sxs-lookup"><span data-stu-id="61005-130">The host's custom data must be the same size for every I/O request.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="61005-131">物件本身的大小 `OVERLAPPED` 不包含在的值中 `pcbSize` 。</span><span class="sxs-lookup"><span data-stu-id="61005-131">The size of the `OVERLAPPED` object itself is not included in the value of `pcbSize`.</span></span>  
  
 <span data-ttu-id="61005-132">如需結構的詳細資訊 `OVERLAPPED` ，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="61005-132">For more information about the `OVERLAPPED` structure, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61005-133">需求</span><span class="sxs-lookup"><span data-stu-id="61005-133">Requirements</span></span>  

 <span data-ttu-id="61005-134">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61005-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61005-135">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="61005-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61005-136">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="61005-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61005-137">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61005-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61005-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61005-138">See also</span></span>

- <xref:System.Threading.NativeOverlapped>
- [<span data-ttu-id="61005-139">ICLRIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="61005-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="61005-140">IHostIoCompletionManager 介面</span><span class="sxs-lookup"><span data-stu-id="61005-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
