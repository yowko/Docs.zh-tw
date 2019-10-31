---
title: ICLRProbingAssemblyEnum::Get 方法
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 2ff1f9428a92d091a51a4cca12d69d98da0ecba2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120529"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="a29d7-102">ICLRProbingAssemblyEnum::Get 方法</span><span class="sxs-lookup"><span data-stu-id="a29d7-102">ICLRProbingAssemblyEnum::Get Method</span></span>
<span data-ttu-id="a29d7-103">取得指定索引處的元件識別。</span><span class="sxs-lookup"><span data-stu-id="a29d7-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29d7-104">語法</span><span class="sxs-lookup"><span data-stu-id="a29d7-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a29d7-105">參數</span><span class="sxs-lookup"><span data-stu-id="a29d7-105">Parameters</span></span>  
 `dwIndex`  
 <span data-ttu-id="a29d7-106">在要傳回之元件身分識別的以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="a29d7-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a29d7-107">脫銷包含元件識別資料的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a29d7-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a29d7-108">[in、out]`pwzBuffer` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="a29d7-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a29d7-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a29d7-109">Return Value</span></span>  
  
|<span data-ttu-id="a29d7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a29d7-110">HRESULT</span></span>|<span data-ttu-id="a29d7-111">描述</span><span class="sxs-lookup"><span data-stu-id="a29d7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a29d7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a29d7-112">S_OK</span></span>|<span data-ttu-id="a29d7-113">已成功傳回 `Get`。</span><span class="sxs-lookup"><span data-stu-id="a29d7-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="a29d7-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a29d7-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a29d7-115">`pwzBuffer` 太小。</span><span class="sxs-lookup"><span data-stu-id="a29d7-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a29d7-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="a29d7-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="a29d7-117">列舉不包含其他專案。</span><span class="sxs-lookup"><span data-stu-id="a29d7-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="a29d7-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a29d7-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a29d7-119">Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="a29d7-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a29d7-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a29d7-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a29d7-121">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="a29d7-121">The call timed out.</span></span>|  
|<span data-ttu-id="a29d7-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a29d7-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a29d7-123">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="a29d7-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a29d7-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a29d7-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a29d7-125">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="a29d7-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a29d7-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a29d7-126">E_FAIL</span></span>|<span data-ttu-id="a29d7-127">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="a29d7-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a29d7-128">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="a29d7-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a29d7-129">對任何裝載方法的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="a29d7-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a29d7-130">備註</span><span class="sxs-lookup"><span data-stu-id="a29d7-130">Remarks</span></span>  
 <span data-ttu-id="a29d7-131">位於索引0的識別是處理器架構特有的身分識別。</span><span class="sxs-lookup"><span data-stu-id="a29d7-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="a29d7-132">位於索引1的識別是 Microsoft 中繼語言（MSIL）的架構中立元件。</span><span class="sxs-lookup"><span data-stu-id="a29d7-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a29d7-133">位於索引2的識別不包含架構資訊。</span><span class="sxs-lookup"><span data-stu-id="a29d7-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="a29d7-134">`Get` 通常會被呼叫兩次。</span><span class="sxs-lookup"><span data-stu-id="a29d7-134">`Get` is typically called twice.</span></span> <span data-ttu-id="a29d7-135">第一個呼叫會為 `pwzBuffer`提供 null 值，並將 `pcchBufferSize` 設定為適用于 `pwzBuffer`的大小。</span><span class="sxs-lookup"><span data-stu-id="a29d7-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="a29d7-136">第二個呼叫會提供適當大小的 `pwzBuffer`，並在完成時包含標準的元件識別資料。</span><span class="sxs-lookup"><span data-stu-id="a29d7-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a29d7-137">需求</span><span class="sxs-lookup"><span data-stu-id="a29d7-137">Requirements</span></span>  
 <span data-ttu-id="a29d7-138">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a29d7-138">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a29d7-139">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="a29d7-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a29d7-140">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a29d7-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a29d7-141">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a29d7-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a29d7-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="a29d7-142">See also</span></span>

- [<span data-ttu-id="a29d7-143">ICLRProbingAssemblyEnum 介面</span><span class="sxs-lookup"><span data-stu-id="a29d7-143">ICLRProbingAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="a29d7-144">ICLRAssemblyIdentityManager 介面</span><span class="sxs-lookup"><span data-stu-id="a29d7-144">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
