---
title: ICLRRuntimeHost::GetCurrentAppDomainId 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 2b1c9e99604664c99960a0741de6eae6b38fe963
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728845"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="91c34-102">ICLRRuntimeHost::GetCurrentAppDomainId 方法</span><span class="sxs-lookup"><span data-stu-id="91c34-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="91c34-103">取得目前正在執行之的數值識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="91c34-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91c34-104">語法</span><span class="sxs-lookup"><span data-stu-id="91c34-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91c34-105">參數</span><span class="sxs-lookup"><span data-stu-id="91c34-105">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="91c34-106">擴展目前正在執行之的數值識別碼 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="91c34-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91c34-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="91c34-107">Return Value</span></span>  
  
|<span data-ttu-id="91c34-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91c34-108">HRESULT</span></span>|<span data-ttu-id="91c34-109">描述</span><span class="sxs-lookup"><span data-stu-id="91c34-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91c34-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="91c34-110">S_OK</span></span>|<span data-ttu-id="91c34-111">`GetCurrentAppDomainId` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="91c34-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="91c34-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91c34-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91c34-113">Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="91c34-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91c34-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91c34-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91c34-115">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="91c34-115">The call timed out.</span></span>|  
|<span data-ttu-id="91c34-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91c34-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91c34-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="91c34-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91c34-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91c34-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91c34-119">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="91c34-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91c34-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91c34-120">E_FAIL</span></span>|<span data-ttu-id="91c34-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="91c34-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91c34-122">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="91c34-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91c34-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="91c34-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91c34-124">備註</span><span class="sxs-lookup"><span data-stu-id="91c34-124">Remarks</span></span>  

 <span data-ttu-id="91c34-125">`pdwAppDomainId`參數會設定為 <xref:System.AppDomain.Id%2A> 目前線程執行所在之的屬性值 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="91c34-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91c34-126">需求</span><span class="sxs-lookup"><span data-stu-id="91c34-126">Requirements</span></span>  

 <span data-ttu-id="91c34-127">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91c34-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91c34-128">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="91c34-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91c34-129">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="91c34-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91c34-130">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91c34-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91c34-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91c34-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="91c34-132">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="91c34-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
