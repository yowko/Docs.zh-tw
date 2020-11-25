---
title: ICLRReferenceAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRReferenceAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRReferenceAssemblyEnum::Get
helpviewer_keywords:
- ICLRReferenceAssemblyEnum::Get method [.NET Framework hosting]
- Get method, ICLRReferenceAssemblyEnum interface [.NET Framework hosting]
ms.assetid: f21c1612-9c5d-4abc-a337-577086d29c17
topic_type:
- apiref
ms.openlocfilehash: 3968adf418fcea847ee2be5a412385d041a53544
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728898"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="e37bd-102">ICLRReferenceAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="e37bd-102">ICLRReferenceAssemblyEnum::Get Method</span></span>

<span data-ttu-id="e37bd-103">取得提供的索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="e37bd-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e37bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="e37bd-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e37bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="e37bd-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="e37bd-106">在要傳回的元件識別之以零為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="e37bd-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="e37bd-107">擴展包含元件身分識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e37bd-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="e37bd-108">[in，out]緩衝區的大小 `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="e37bd-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e37bd-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="e37bd-109">Return Value</span></span>  
  
|<span data-ttu-id="e37bd-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e37bd-110">HRESULT</span></span>|<span data-ttu-id="e37bd-111">描述</span><span class="sxs-lookup"><span data-stu-id="e37bd-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e37bd-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e37bd-112">S_OK</span></span>|<span data-ttu-id="e37bd-113">`Get` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="e37bd-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="e37bd-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="e37bd-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="e37bd-115">`pwzBuffer` 太小了。</span><span class="sxs-lookup"><span data-stu-id="e37bd-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="e37bd-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="e37bd-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="e37bd-117">列舉中不包含任何專案。</span><span class="sxs-lookup"><span data-stu-id="e37bd-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="e37bd-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e37bd-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e37bd-119">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e37bd-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e37bd-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e37bd-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e37bd-121">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="e37bd-121">The call timed out.</span></span>|  
|<span data-ttu-id="e37bd-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e37bd-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e37bd-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e37bd-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e37bd-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e37bd-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e37bd-125">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="e37bd-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e37bd-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e37bd-126">E_FAIL</span></span>|<span data-ttu-id="e37bd-127">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e37bd-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e37bd-128">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="e37bd-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e37bd-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e37bd-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e37bd-130">備註</span><span class="sxs-lookup"><span data-stu-id="e37bd-130">Remarks</span></span>  

 <span data-ttu-id="e37bd-131">`Get` 通常會呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="e37bd-131">`Get` is typically called twice.</span></span> <span data-ttu-id="e37bd-132">第一個呼叫會提供的 null 值 `pwzBuffer` ，並將設定 `pcchBufferSize` 為適合的大小 `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="e37bd-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="e37bd-133">第二個呼叫會提供適當大小 `pwzBuffer` ，並在完成時包含標準的元件身分識別資料。</span><span class="sxs-lookup"><span data-stu-id="e37bd-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e37bd-134">需求</span><span class="sxs-lookup"><span data-stu-id="e37bd-134">Requirements</span></span>  

 <span data-ttu-id="e37bd-135">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e37bd-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e37bd-136">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e37bd-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e37bd-137">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e37bd-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e37bd-138">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e37bd-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37bd-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e37bd-139">See also</span></span>

- [<span data-ttu-id="e37bd-140">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="e37bd-140">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="e37bd-141">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="e37bd-141">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
