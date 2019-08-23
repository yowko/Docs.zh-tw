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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fcadb708638efb0b7946426c538e01661505dfa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912246"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="83bdc-102">ICLRRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="83bdc-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="83bdc-103">由 common language runtime (CLR) 停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="83bdc-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="83bdc-104">這個方法不會將資源釋放到主機、卸載應用程式域或終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="83bdc-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="83bdc-105">您必須終止進程以釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="83bdc-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83bdc-106">語法</span><span class="sxs-lookup"><span data-stu-id="83bdc-106">Syntax</span></span>  
  
```cpp  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="83bdc-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="83bdc-107">Return Value</span></span>  
  
|<span data-ttu-id="83bdc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83bdc-108">HRESULT</span></span>|<span data-ttu-id="83bdc-109">描述</span><span class="sxs-lookup"><span data-stu-id="83bdc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83bdc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="83bdc-110">S_OK</span></span>|<span data-ttu-id="83bdc-111">`Stop`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="83bdc-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="83bdc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83bdc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83bdc-113">CLR 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="83bdc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83bdc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83bdc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83bdc-115">呼叫超時。</span><span class="sxs-lookup"><span data-stu-id="83bdc-115">The call timed out.</span></span>|  
|<span data-ttu-id="83bdc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83bdc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83bdc-117">呼叫端沒有擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="83bdc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83bdc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83bdc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83bdc-119">已封鎖的執行緒或光纖在等候時取消了事件。</span><span class="sxs-lookup"><span data-stu-id="83bdc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83bdc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83bdc-120">E_FAIL</span></span>|<span data-ttu-id="83bdc-121">發生不明的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="83bdc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83bdc-122">如果方法傳回 E_FAIL, 則 CLR 在進程內將無法再使用。</span><span class="sxs-lookup"><span data-stu-id="83bdc-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83bdc-123">對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="83bdc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83bdc-124">需求</span><span class="sxs-lookup"><span data-stu-id="83bdc-124">Requirements</span></span>  
 <span data-ttu-id="83bdc-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="83bdc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83bdc-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83bdc-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83bdc-127">**LIBRARY:** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="83bdc-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83bdc-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83bdc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83bdc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83bdc-129">See also</span></span>

- [<span data-ttu-id="83bdc-130">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="83bdc-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
