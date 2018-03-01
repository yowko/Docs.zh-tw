---
title: "ICLRRuntimeHost::Stop 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3cb9eaecdec661ae56727e5fd38c7e9a3b9621d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="c4936-102">ICLRRuntimeHost::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="c4936-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="c4936-103">停止執行的程式碼，common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="c4936-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c4936-104">這個方法不釋放資源給主機、 卸載應用程式定義域或終結執行緒。</span><span class="sxs-lookup"><span data-stu-id="c4936-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="c4936-105">您必須終止處理序釋放這些資源。</span><span class="sxs-lookup"><span data-stu-id="c4936-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4936-106">語法</span><span class="sxs-lookup"><span data-stu-id="c4936-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c4936-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4936-107">Return Value</span></span>  
  
|<span data-ttu-id="c4936-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4936-108">HRESULT</span></span>|<span data-ttu-id="c4936-109">描述</span><span class="sxs-lookup"><span data-stu-id="c4936-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4936-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4936-110">S_OK</span></span>|<span data-ttu-id="c4936-111">`Stop`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c4936-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="c4936-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4936-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4936-113">CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="c4936-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4936-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4936-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4936-115">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="c4936-115">The call timed out.</span></span>|  
|<span data-ttu-id="c4936-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4936-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4936-117">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="c4936-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4936-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4936-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4936-119">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="c4936-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4936-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4936-120">E_FAIL</span></span>|<span data-ttu-id="c4936-121">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="c4936-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4936-122">若方法會傳回 E_FAIL，CLR 就不會再處理序內。</span><span class="sxs-lookup"><span data-stu-id="c4936-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4936-123">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="c4936-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c4936-124">需求</span><span class="sxs-lookup"><span data-stu-id="c4936-124">Requirements</span></span>  
 <span data-ttu-id="c4936-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4936-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4936-126">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4936-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4936-127">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4936-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4936-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4936-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4936-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4936-129">See Also</span></span>  
 [<span data-ttu-id="c4936-130">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c4936-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
