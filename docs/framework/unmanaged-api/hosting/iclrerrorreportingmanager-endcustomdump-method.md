---
title: "ICLRErrorReportingManager::EndCustomDump 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.EndCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 709ef121294a92353b21363ae12919e8e147efab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="77f66-102">ICLRErrorReportingManager::EndCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="77f66-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="77f66-103">會移除之前呼叫中指定的自訂堆疊傾印組態[iclrerrorreportingmanager:: Begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="77f66-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f66-104">語法</span><span class="sxs-lookup"><span data-stu-id="77f66-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="77f66-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="77f66-105">Return Value</span></span>  
  
|<span data-ttu-id="77f66-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77f66-106">HRESULT</span></span>|<span data-ttu-id="77f66-107">描述</span><span class="sxs-lookup"><span data-stu-id="77f66-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77f66-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="77f66-108">S_OK</span></span>|<span data-ttu-id="77f66-109">`EndCustomDump`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="77f66-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="77f66-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77f66-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77f66-111">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="77f66-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77f66-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77f66-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77f66-113">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="77f66-113">The call timed out.</span></span>|  
|<span data-ttu-id="77f66-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77f66-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77f66-115">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="77f66-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77f66-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77f66-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77f66-117">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="77f66-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77f66-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77f66-118">E_FAIL</span></span>|<span data-ttu-id="77f66-119">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="77f66-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77f66-120">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="77f66-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77f66-121">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="77f66-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77f66-122">備註</span><span class="sxs-lookup"><span data-stu-id="77f66-122">Remarks</span></span>  
 <span data-ttu-id="77f66-123">`EndCustomDump`方法清除之前呼叫來設定自訂的堆疊傾印組態`BeginCustomDump`方法並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="77f66-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="77f66-124">它應該呼叫自訂的堆疊傾印完成後。</span><span class="sxs-lookup"><span data-stu-id="77f66-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="77f66-125">無法呼叫`EndCustomDump`會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="77f66-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f66-126">需求</span><span class="sxs-lookup"><span data-stu-id="77f66-126">Requirements</span></span>  
 <span data-ttu-id="77f66-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77f66-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77f66-128">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77f66-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77f66-129">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="77f66-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77f66-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77f66-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f66-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="77f66-131">See Also</span></span>  
 [<span data-ttu-id="77f66-132">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="77f66-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="77f66-133">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="77f66-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="77f66-134">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="77f66-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
