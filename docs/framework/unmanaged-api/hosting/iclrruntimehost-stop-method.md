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
ms.openlocfilehash: 71d4167d17b20c08c2cbc62d2ac0c1cddd88e527
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634423"
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="19a85-102">ICLRRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="19a85-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="19a85-103">Common language runtime (CLR)，會停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="19a85-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="19a85-104">這個方法不會釋放資源給主機、 卸載應用程式定義域或終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="19a85-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="19a85-105">您必須終止處理序釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="19a85-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19a85-106">語法</span><span class="sxs-lookup"><span data-stu-id="19a85-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="19a85-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="19a85-107">Return Value</span></span>  
  
|<span data-ttu-id="19a85-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="19a85-108">HRESULT</span></span>|<span data-ttu-id="19a85-109">描述</span><span class="sxs-lookup"><span data-stu-id="19a85-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19a85-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="19a85-110">S_OK</span></span>|<span data-ttu-id="19a85-111">`Stop` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="19a85-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="19a85-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="19a85-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="19a85-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="19a85-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="19a85-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="19a85-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="19a85-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="19a85-115">The call timed out.</span></span>|  
|<span data-ttu-id="19a85-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="19a85-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="19a85-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="19a85-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="19a85-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="19a85-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="19a85-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="19a85-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="19a85-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="19a85-120">E_FAIL</span></span>|<span data-ttu-id="19a85-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="19a85-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="19a85-122">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="19a85-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="19a85-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="19a85-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19a85-124">需求</span><span class="sxs-lookup"><span data-stu-id="19a85-124">Requirements</span></span>  
 <span data-ttu-id="19a85-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19a85-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19a85-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="19a85-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19a85-127">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="19a85-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19a85-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19a85-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19a85-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19a85-129">See also</span></span>
- [<span data-ttu-id="19a85-130">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="19a85-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
