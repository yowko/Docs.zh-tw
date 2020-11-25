---
title: ICLRRuntimeHost::UnloadAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: cc5d0d65d213d952c0897a72d8ec38ea6b8b22db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700661"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="aac7a-102">ICLRRuntimeHost::UnloadAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="aac7a-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="aac7a-103">卸載對應于 <xref:System.AppDomain> 指定之數值識別碼的 managed。</span><span class="sxs-lookup"><span data-stu-id="aac7a-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac7a-104">語法</span><span class="sxs-lookup"><span data-stu-id="aac7a-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aac7a-105">參數</span><span class="sxs-lookup"><span data-stu-id="aac7a-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="aac7a-106">在要卸載之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="aac7a-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="aac7a-107">[in] `true` 若要指出 common language runtime ( CLR) 必須等到它完成執行應用程式的目前線程之後，再嘗試卸載應用程式域。</span><span class="sxs-lookup"><span data-stu-id="aac7a-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aac7a-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="aac7a-108">Return Value</span></span>  
  
|<span data-ttu-id="aac7a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aac7a-109">HRESULT</span></span>|<span data-ttu-id="aac7a-110">描述</span><span class="sxs-lookup"><span data-stu-id="aac7a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aac7a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aac7a-111">S_OK</span></span>|<span data-ttu-id="aac7a-112">`UnloadAppDomain` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="aac7a-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="aac7a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aac7a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aac7a-114">CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="aac7a-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aac7a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aac7a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aac7a-116">呼叫已超時。</span><span class="sxs-lookup"><span data-stu-id="aac7a-116">The call timed out.</span></span>|  
|<span data-ttu-id="aac7a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aac7a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aac7a-118">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="aac7a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aac7a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aac7a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aac7a-120">當封鎖的執行緒或光纖正在等候時，已取消事件。</span><span class="sxs-lookup"><span data-stu-id="aac7a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aac7a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aac7a-121">E_FAIL</span></span>|<span data-ttu-id="aac7a-122">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="aac7a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aac7a-123">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="aac7a-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aac7a-124">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="aac7a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aac7a-125">備註</span><span class="sxs-lookup"><span data-stu-id="aac7a-125">Remarks</span></span>  

 <span data-ttu-id="aac7a-126">您可以藉由呼叫 [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)來取得目前線程執行所在之應用程式域的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="aac7a-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="aac7a-127">此識別碼對應于 <xref:System.AppDomain.Id%2A> managed 類型的屬性 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="aac7a-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac7a-128">需求</span><span class="sxs-lookup"><span data-stu-id="aac7a-128">Requirements</span></span>  

 <span data-ttu-id="aac7a-129">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aac7a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac7a-130">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="aac7a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aac7a-131">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="aac7a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aac7a-132">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac7a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac7a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aac7a-133">See also</span></span>

- [<span data-ttu-id="aac7a-134">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="aac7a-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
