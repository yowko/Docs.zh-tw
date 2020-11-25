---
title: IHostThreadPoolManager::QueueUserWorkItem 方法
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.QueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::QueueUserWorkItem
helpviewer_keywords:
- IHostThreadPoolManager::QueueUserWorkItem method [.NET Framework hosting]
- QueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 41602053-8670-4827-9d61-cbfcba509b9c
topic_type:
- apiref
ms.openlocfilehash: 4537d367518dd80b2559f8ca058684e234ff7a91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730743"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="a00e3-102">IHostThreadPoolManager::QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="a00e3-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>

<span data-ttu-id="a00e3-103">將函式排入佇列以便執行，並指定包含該函式所要使用之資料的物件。</span><span class="sxs-lookup"><span data-stu-id="a00e3-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="a00e3-104">當執行緒變成可用時，就會執行此函式。</span><span class="sxs-lookup"><span data-stu-id="a00e3-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a00e3-105">語法</span><span class="sxs-lookup"><span data-stu-id="a00e3-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a00e3-106">參數</span><span class="sxs-lookup"><span data-stu-id="a00e3-106">Parameters</span></span>  

 `Function`  
 <span data-ttu-id="a00e3-107">在代表要執行之函數的函式指標。</span><span class="sxs-lookup"><span data-stu-id="a00e3-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="a00e3-108">在物件，其中包含要使用的資料 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="a00e3-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="a00e3-109">在針對 Win32 方法所定義的其中一個旗標值， `QueueUserWorkItem` 可控制執行。</span><span class="sxs-lookup"><span data-stu-id="a00e3-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a00e3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="a00e3-110">Return Value</span></span>  
  
|<span data-ttu-id="a00e3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a00e3-111">HRESULT</span></span>|<span data-ttu-id="a00e3-112">描述</span><span class="sxs-lookup"><span data-stu-id="a00e3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a00e3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a00e3-113">S_OK</span></span>|<span data-ttu-id="a00e3-114">`QueueUserWorkItem` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="a00e3-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="a00e3-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a00e3-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a00e3-116">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a00e3-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a00e3-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a00e3-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a00e3-118">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="a00e3-118">The call timed out.</span></span>|  
|<span data-ttu-id="a00e3-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a00e3-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a00e3-120">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a00e3-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a00e3-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a00e3-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a00e3-122">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="a00e3-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a00e3-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a00e3-123">E_FAIL</span></span>|<span data-ttu-id="a00e3-124">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a00e3-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a00e3-125">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a00e3-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a00e3-126">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a00e3-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a00e3-127">備註</span><span class="sxs-lookup"><span data-stu-id="a00e3-127">Remarks</span></span>  

 <span data-ttu-id="a00e3-128">`QueueUserWorkItem` 將工作專案排入執行緒集區中的背景工作執行緒佇列。</span><span class="sxs-lookup"><span data-stu-id="a00e3-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="a00e3-129">其簽章和參數類型與對應的 Win32 函數（具有相同名稱）相同。</span><span class="sxs-lookup"><span data-stu-id="a00e3-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="a00e3-130">如需詳細資訊，請參閱 Windows 平臺檔。</span><span class="sxs-lookup"><span data-stu-id="a00e3-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a00e3-131">需求</span><span class="sxs-lookup"><span data-stu-id="a00e3-131">Requirements</span></span>  

 <span data-ttu-id="a00e3-132">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a00e3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a00e3-133">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a00e3-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a00e3-134">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="a00e3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a00e3-135">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a00e3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a00e3-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a00e3-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="a00e3-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="a00e3-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
