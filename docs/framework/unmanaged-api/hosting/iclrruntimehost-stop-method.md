---
title: ICLRRuntimeHost::Stop 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type:
- apiref
ms.openlocfilehash: 55cd444ffedc92ba74239421ae548ffd930e6ab7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703939"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="e6e8d-102">ICLRRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="e6e8d-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="e6e8d-103">由 common language runtime （CLR）停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e6e8d-104">這個方法不會將資源釋放到主機、卸載應用程式域或終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="e6e8d-105">您必須終止進程以釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e8d-106">語法</span><span class="sxs-lookup"><span data-stu-id="e6e8d-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e6e8d-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="e6e8d-107">Return Value</span></span>  
  
|<span data-ttu-id="e6e8d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6e8d-108">HRESULT</span></span>|<span data-ttu-id="e6e8d-109">說明</span><span class="sxs-lookup"><span data-stu-id="e6e8d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6e8d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6e8d-110">S_OK</span></span>|<span data-ttu-id="e6e8d-111">`Stop`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="e6e8d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6e8d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6e8d-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e6e8d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e6e8d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e6e8d-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-115">The call timed out.</span></span>|  
|<span data-ttu-id="e6e8d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e6e8d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e6e8d-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e6e8d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e6e8d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e6e8d-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e6e8d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6e8d-120">E_FAIL</span></span>|<span data-ttu-id="e6e8d-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e6e8d-122">如果方法傳回 E_FAIL，就無法在進程內使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e6e8d-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6e8d-124">需求</span><span class="sxs-lookup"><span data-stu-id="e6e8d-124">Requirements</span></span>  
 <span data-ttu-id="e6e8d-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6e8d-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e8d-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="e6e8d-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6e8d-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e6e8d-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e8d-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6e8d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e8d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6e8d-129">See also</span></span>

- [<span data-ttu-id="e6e8d-130">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e6e8d-130">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
