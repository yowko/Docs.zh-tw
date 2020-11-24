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
ms.openlocfilehash: d4c9048c89d55ed048a55a771572823905a056df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687121"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="117d3-102">IHostMAlloc::Free 方法</span><span class="sxs-lookup"><span data-stu-id="117d3-102">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="117d3-103">釋放使用 [配置函數配置的記憶體](ihostmalloc-alloc-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="117d3-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="117d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="117d3-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="117d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="117d3-105">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="117d3-106">在要釋放之記憶體的指標。</span><span class="sxs-lookup"><span data-stu-id="117d3-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="117d3-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="117d3-107">Return Value</span></span>  
  
|<span data-ttu-id="117d3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="117d3-108">HRESULT</span></span>|<span data-ttu-id="117d3-109">描述</span><span class="sxs-lookup"><span data-stu-id="117d3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="117d3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="117d3-110">S_OK</span></span>|<span data-ttu-id="117d3-111">`Free` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="117d3-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="117d3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="117d3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="117d3-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="117d3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="117d3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="117d3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="117d3-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="117d3-115">The call timed out.</span></span>|  
|<span data-ttu-id="117d3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="117d3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="117d3-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="117d3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="117d3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="117d3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="117d3-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="117d3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="117d3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="117d3-120">E_FAIL</span></span>|<span data-ttu-id="117d3-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="117d3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="117d3-122">當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="117d3-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="117d3-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="117d3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="117d3-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="117d3-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="117d3-125">嘗試釋放未透過主機配置的記憶體。</span><span class="sxs-lookup"><span data-stu-id="117d3-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="117d3-126">備註</span><span class="sxs-lookup"><span data-stu-id="117d3-126">Remarks</span></span>  

 <span data-ttu-id="117d3-127">如果 `pMem` 參數所參考的記憶體區域未使用的呼叫來配置 `Alloc` ，主機應該會傳回 HOST_E_INVALIDOPERATION。</span><span class="sxs-lookup"><span data-stu-id="117d3-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="117d3-128">需求</span><span class="sxs-lookup"><span data-stu-id="117d3-128">Requirements</span></span>  

 <span data-ttu-id="117d3-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="117d3-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="117d3-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="117d3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="117d3-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="117d3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="117d3-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="117d3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="117d3-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="117d3-133">See also</span></span>

- [<span data-ttu-id="117d3-134">IHostMemoryManager 介面</span><span class="sxs-lookup"><span data-stu-id="117d3-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="117d3-135">IHostMalloc 介面</span><span class="sxs-lookup"><span data-stu-id="117d3-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
