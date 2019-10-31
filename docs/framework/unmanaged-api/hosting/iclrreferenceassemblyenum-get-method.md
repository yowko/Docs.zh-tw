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
ms.openlocfilehash: 8f479443e168c3fc7c627c3227e59f1e8b54f0e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120509"
---
# <a name="iclrreferenceassemblyenumget-method"></a><span data-ttu-id="f7c56-102">ICLRReferenceAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="f7c56-102">ICLRReferenceAssemblyEnum::Get Method</span></span>
<span data-ttu-id="f7c56-103">取得所提供索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="f7c56-103">Gets the assembly identity at the supplied index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c56-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7c56-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7c56-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7c56-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="f7c56-106">在要傳回之元件身分識別的以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="f7c56-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="f7c56-107">脫銷包含元件識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f7c56-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="f7c56-108">[in、out]`pwzBuffer` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="f7c56-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7c56-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7c56-109">Return Value</span></span>  
  
|<span data-ttu-id="f7c56-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7c56-110">HRESULT</span></span>|<span data-ttu-id="f7c56-111">描述</span><span class="sxs-lookup"><span data-stu-id="f7c56-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7c56-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7c56-112">S_OK</span></span>|<span data-ttu-id="f7c56-113">已成功傳回 `Get`。</span><span class="sxs-lookup"><span data-stu-id="f7c56-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="f7c56-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f7c56-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f7c56-115">`pwzBuffer` 太小。</span><span class="sxs-lookup"><span data-stu-id="f7c56-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="f7c56-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="f7c56-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="f7c56-117">列舉不包含其他專案。</span><span class="sxs-lookup"><span data-stu-id="f7c56-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="f7c56-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7c56-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7c56-119">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="f7c56-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7c56-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7c56-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7c56-121">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="f7c56-121">The call timed out.</span></span>|  
|<span data-ttu-id="f7c56-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7c56-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7c56-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="f7c56-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7c56-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7c56-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7c56-125">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="f7c56-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7c56-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7c56-126">E_FAIL</span></span>|<span data-ttu-id="f7c56-127">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="f7c56-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7c56-128">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="f7c56-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7c56-129">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="f7c56-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7c56-130">備註</span><span class="sxs-lookup"><span data-stu-id="f7c56-130">Remarks</span></span>  
 <span data-ttu-id="f7c56-131">`Get` 通常會被呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="f7c56-131">`Get` is typically called twice.</span></span> <span data-ttu-id="f7c56-132">第一個呼叫會為 `pwzBuffer`提供 null 值，並將 `pcchBufferSize` 設定為適用于 `pwzBuffer`的大小。</span><span class="sxs-lookup"><span data-stu-id="f7c56-132">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="f7c56-133">第二個呼叫會提供適當大小的 `pwzBuffer`，並在完成時包含標準的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="f7c56-133">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c56-134">需求</span><span class="sxs-lookup"><span data-stu-id="f7c56-134">Requirements</span></span>  
 <span data-ttu-id="f7c56-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7c56-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c56-136">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="f7c56-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7c56-137">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f7c56-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7c56-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c56-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c56-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7c56-139">See also</span></span>

- [<span data-ttu-id="f7c56-140">ICLRAssemblyReferenceList 介面</span><span class="sxs-lookup"><span data-stu-id="f7c56-140">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f7c56-141">ICLRReferenceAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f7c56-141">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
