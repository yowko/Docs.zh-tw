---
title: "ICLRRuntimeHost::GetCLRControl 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc8cc80e24e3dd03d3c179d91fe16b8391502bf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="b1df4-102">ICLRRuntimeHost::GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="b1df4-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="b1df4-103">取得類型的介面指標[ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主機可用於自訂的 common language runtime (CLR) 層面。</span><span class="sxs-lookup"><span data-stu-id="b1df4-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1df4-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1df4-104">Syntax</span></span>  
  
```  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1df4-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1df4-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="b1df4-106">[out]類型的介面指標[ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)，可讓主機設定的 CLR 的其他層面。</span><span class="sxs-lookup"><span data-stu-id="b1df4-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1df4-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1df4-107">Return Value</span></span>  
  
|<span data-ttu-id="b1df4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1df4-108">HRESULT</span></span>|<span data-ttu-id="b1df4-109">描述</span><span class="sxs-lookup"><span data-stu-id="b1df4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1df4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1df4-110">S_OK</span></span>|<span data-ttu-id="b1df4-111">`GetCLRControl`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b1df4-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="b1df4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1df4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1df4-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="b1df4-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1df4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1df4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1df4-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="b1df4-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1df4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1df4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1df4-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="b1df4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1df4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1df4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1df4-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="b1df4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1df4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1df4-120">E_FAIL</span></span>|<span data-ttu-id="b1df4-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="b1df4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1df4-122">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="b1df4-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1df4-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="b1df4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1df4-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b1df4-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b1df4-125">CLR 已啟動。</span><span class="sxs-lookup"><span data-stu-id="b1df4-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1df4-126">備註</span><span class="sxs-lookup"><span data-stu-id="b1df4-126">Remarks</span></span>  
 <span data-ttu-id="b1df4-127">`ICLRControl`提供[GetCLRManager 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法，可讓主應用程式取得其中一種管理員類型的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b1df4-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1df4-128">需求</span><span class="sxs-lookup"><span data-stu-id="b1df4-128">Requirements</span></span>  
 <span data-ttu-id="b1df4-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1df4-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1df4-130">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1df4-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1df4-131">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b1df4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1df4-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1df4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1df4-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1df4-133">See Also</span></span>  
 [<span data-ttu-id="b1df4-134">ICLRControl 介面</span><span class="sxs-lookup"><span data-stu-id="b1df4-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="b1df4-135">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b1df4-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
