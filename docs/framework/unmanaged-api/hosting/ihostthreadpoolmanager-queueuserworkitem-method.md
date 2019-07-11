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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12c571f478f15a0b72168977f12623be1c4a08a9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749156"
---
# <a name="ihostthreadpoolmanagerqueueuserworkitem-method"></a><span data-ttu-id="51a61-102">IHostThreadPoolManager::QueueUserWorkItem 方法</span><span class="sxs-lookup"><span data-stu-id="51a61-102">IHostThreadPoolManager::QueueUserWorkItem Method</span></span>
<span data-ttu-id="51a61-103">函式，以執行排入佇列，並指定包含該函式所使用的資料的物件。</span><span class="sxs-lookup"><span data-stu-id="51a61-103">Queues a function for execution, and specifies an object containing data to be used by that function.</span></span> <span data-ttu-id="51a61-104">當執行緒變成可用時，就會執行函式。</span><span class="sxs-lookup"><span data-stu-id="51a61-104">The function executes when a thread becomes available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51a61-105">語法</span><span class="sxs-lookup"><span data-stu-id="51a61-105">Syntax</span></span>  
  
```cpp  
HRESULT QueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID Context,  
    [in] ULONG Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51a61-106">參數</span><span class="sxs-lookup"><span data-stu-id="51a61-106">Parameters</span></span>  
 `Function`  
 <span data-ttu-id="51a61-107">[in]函式指標，表示要執行的函式。</span><span class="sxs-lookup"><span data-stu-id="51a61-107">[in] A function pointer that represents the function to execute.</span></span>  
  
 `Context`  
 <span data-ttu-id="51a61-108">[in]物件，包含資料，以供`Function`。</span><span class="sxs-lookup"><span data-stu-id="51a61-108">[in] An object that contains data to be used by `Function`.</span></span>  
  
 `Flags`  
 <span data-ttu-id="51a61-109">[in]其中一個旗標值，如 win32 定義`QueueUserWorkItem`方法，可控制執行。</span><span class="sxs-lookup"><span data-stu-id="51a61-109">[in] One of the flags values, as defined for the Win32 `QueueUserWorkItem` method, that control execution.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51a61-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="51a61-110">Return Value</span></span>  
  
|<span data-ttu-id="51a61-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51a61-111">HRESULT</span></span>|<span data-ttu-id="51a61-112">描述</span><span class="sxs-lookup"><span data-stu-id="51a61-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51a61-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="51a61-113">S_OK</span></span>|<span data-ttu-id="51a61-114">`QueueUserWorkItem` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="51a61-114">`QueueUserWorkItem` returned successfully.</span></span>|  
|<span data-ttu-id="51a61-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51a61-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51a61-116">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="51a61-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51a61-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51a61-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51a61-118">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="51a61-118">The call timed out.</span></span>|  
|<span data-ttu-id="51a61-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51a61-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51a61-120">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="51a61-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51a61-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51a61-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51a61-122">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="51a61-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51a61-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51a61-123">E_FAIL</span></span>|<span data-ttu-id="51a61-124">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="51a61-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51a61-125">方法會傳回 E_FAIL CLR 已不再可在此程序中使用。</span><span class="sxs-lookup"><span data-stu-id="51a61-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51a61-126">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="51a61-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51a61-127">備註</span><span class="sxs-lookup"><span data-stu-id="51a61-127">Remarks</span></span>  
 <span data-ttu-id="51a61-128">`QueueUserWorkItem` 排入佇列的背景工作執行緒的執行緒集區中的工作項目。</span><span class="sxs-lookup"><span data-stu-id="51a61-128">`QueueUserWorkItem` queues a work item to a worker thread in the thread pool.</span></span> <span data-ttu-id="51a61-129">其簽章和參數型別都完全相同的對應的 Win32 函式，其具有相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="51a61-129">Its signature and parameter types are identical to those of the corresponding Win32 function, which has the same name.</span></span> <span data-ttu-id="51a61-130">如需詳細資訊，請參閱 Windows 平台的文件。</span><span class="sxs-lookup"><span data-stu-id="51a61-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51a61-131">需求</span><span class="sxs-lookup"><span data-stu-id="51a61-131">Requirements</span></span>  
 <span data-ttu-id="51a61-132">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51a61-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51a61-133">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="51a61-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51a61-134">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51a61-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51a61-135">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51a61-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51a61-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51a61-136">See also</span></span>

- <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="51a61-137">IHostThreadPoolManager 介面</span><span class="sxs-lookup"><span data-stu-id="51a61-137">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
