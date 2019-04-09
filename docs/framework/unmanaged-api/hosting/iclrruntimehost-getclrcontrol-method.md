---
title: ICLRRuntimeHost::GetCLRControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83b029c24321946f777966daa7a486f9e8e7b7a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073144"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="02b65-102">ICLRRuntimeHost::GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="02b65-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="02b65-103">取得類型的介面指標[ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主機可用於自訂的 common language runtime (CLR) 的層面。</span><span class="sxs-lookup"><span data-stu-id="02b65-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02b65-104">語法</span><span class="sxs-lookup"><span data-stu-id="02b65-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02b65-105">參數</span><span class="sxs-lookup"><span data-stu-id="02b65-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="02b65-106">[out]類型的介面指標[ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)，可讓主機設定的 CLR 的其他層面。</span><span class="sxs-lookup"><span data-stu-id="02b65-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02b65-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="02b65-107">Return Value</span></span>  
  
|<span data-ttu-id="02b65-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02b65-108">HRESULT</span></span>|<span data-ttu-id="02b65-109">描述</span><span class="sxs-lookup"><span data-stu-id="02b65-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02b65-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="02b65-110">S_OK</span></span>|`GetCLRControl` <span data-ttu-id="02b65-111">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="02b65-111">returned successfully.</span></span>|  
|<span data-ttu-id="02b65-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="02b65-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="02b65-113">不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="02b65-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="02b65-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="02b65-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="02b65-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="02b65-115">The call timed out.</span></span>|  
|<span data-ttu-id="02b65-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="02b65-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="02b65-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="02b65-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="02b65-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="02b65-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="02b65-119">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="02b65-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="02b65-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="02b65-120">E_FAIL</span></span>|<span data-ttu-id="02b65-121">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="02b65-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="02b65-122">如果方法會傳回 E_FAIL，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="02b65-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="02b65-123">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="02b65-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="02b65-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="02b65-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="02b65-125">已經啟動 CLR。</span><span class="sxs-lookup"><span data-stu-id="02b65-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02b65-126">備註</span><span class="sxs-lookup"><span data-stu-id="02b65-126">Remarks</span></span>  
 `ICLRControl` <span data-ttu-id="02b65-127">提供[GetCLRManager 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法，可讓主應用程式取得的介面指標，其中一種管理員類型。</span><span class="sxs-lookup"><span data-stu-id="02b65-127">provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02b65-128">需求</span><span class="sxs-lookup"><span data-stu-id="02b65-128">Requirements</span></span>  
 <span data-ttu-id="02b65-129">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02b65-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b65-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="02b65-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02b65-131">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="02b65-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="02b65-132">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="02b65-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="02b65-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02b65-133">See also</span></span>

- [<span data-ttu-id="02b65-134">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="02b65-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="02b65-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="02b65-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
