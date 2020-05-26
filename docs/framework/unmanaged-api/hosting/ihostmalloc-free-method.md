---
title: IHostMAlloc::Free 方法
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: 1dd5ed4c556a5a4d4425a9c0730cebf22ff1785b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804613"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="a82f5-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="a82f5-102">IHostMAlloc::Free Method</span></span>
<span data-ttu-id="a82f5-103">釋放使用配置函[式所配置](ihostmalloc-alloc-method.md)的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a82f5-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a82f5-104">語法</span><span class="sxs-lookup"><span data-stu-id="a82f5-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a82f5-105">參數</span><span class="sxs-lookup"><span data-stu-id="a82f5-105">Parameters</span></span>  
 `pMem`  
 <span data-ttu-id="a82f5-106">在要釋放之記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="a82f5-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a82f5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="a82f5-107">Return Value</span></span>  
  
|<span data-ttu-id="a82f5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a82f5-108">HRESULT</span></span>|<span data-ttu-id="a82f5-109">描述</span><span class="sxs-lookup"><span data-stu-id="a82f5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a82f5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a82f5-110">S_OK</span></span>|<span data-ttu-id="a82f5-111">`Free`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a82f5-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="a82f5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a82f5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a82f5-113">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a82f5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a82f5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a82f5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a82f5-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a82f5-115">The call timed out.</span></span>|  
|<span data-ttu-id="a82f5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a82f5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a82f5-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a82f5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a82f5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a82f5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a82f5-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a82f5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a82f5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a82f5-120">E_FAIL</span></span>|<span data-ttu-id="a82f5-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a82f5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a82f5-122">當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。</span><span class="sxs-lookup"><span data-stu-id="a82f5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a82f5-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a82f5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a82f5-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="a82f5-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="a82f5-125">嘗試釋放未透過主機所配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a82f5-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a82f5-126">備註</span><span class="sxs-lookup"><span data-stu-id="a82f5-126">Remarks</span></span>  
 <span data-ttu-id="a82f5-127">如果 `pMem` 參數參考到未使用呼叫所配置的記憶體區域 `Alloc` ，則主機應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="a82f5-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a82f5-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="a82f5-128">Requirements</span></span>  
 <span data-ttu-id="a82f5-129">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a82f5-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a82f5-130">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a82f5-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a82f5-131">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a82f5-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a82f5-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a82f5-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a82f5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a82f5-133">See also</span></span>

- [<span data-ttu-id="a82f5-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="a82f5-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="a82f5-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="a82f5-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
