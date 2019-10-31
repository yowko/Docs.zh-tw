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
ms.openlocfilehash: 0b59532d18848f1896977aa37f0a9f54a939aa75
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120383"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="c7f71-102">ICLRRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="c7f71-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="c7f71-103">由 common language runtime （CLR）停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7f71-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7f71-104">這個方法不會將資源釋放到主機、卸載應用程式域或終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="c7f71-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="c7f71-105">您必須終止進程以釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="c7f71-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f71-106">語法</span><span class="sxs-lookup"><span data-stu-id="c7f71-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c7f71-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c7f71-107">Return Value</span></span>  
  
|<span data-ttu-id="c7f71-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7f71-108">HRESULT</span></span>|<span data-ttu-id="c7f71-109">描述</span><span class="sxs-lookup"><span data-stu-id="c7f71-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7f71-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7f71-110">S_OK</span></span>|<span data-ttu-id="c7f71-111">已成功傳回 `Stop`。</span><span class="sxs-lookup"><span data-stu-id="c7f71-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="c7f71-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7f71-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7f71-113">CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c7f71-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7f71-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7f71-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7f71-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="c7f71-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7f71-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7f71-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7f71-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c7f71-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7f71-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7f71-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7f71-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="c7f71-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7f71-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7f71-120">E_FAIL</span></span>|<span data-ttu-id="c7f71-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c7f71-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7f71-122">如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="c7f71-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7f71-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c7f71-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7f71-124">需求</span><span class="sxs-lookup"><span data-stu-id="c7f71-124">Requirements</span></span>  
 <span data-ttu-id="c7f71-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f71-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f71-126">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="c7f71-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7f71-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c7f71-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7f71-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f71-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7f71-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="c7f71-129">See also</span></span>

- [<span data-ttu-id="c7f71-130">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c7f71-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
