---
title: "ICLRErrorReportingManager::BeginCustomDump 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c90357f969b19c767d4bb45d4d3105f50cd5682a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="fd425-102">ICLRErrorReportingManager::BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="fd425-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="fd425-103">指定錯誤報告的自訂堆積傾印的組態。</span><span class="sxs-lookup"><span data-stu-id="fd425-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd425-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd425-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd425-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd425-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="fd425-106">[in]A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)值，指出在其上建置自訂堆積傾印堆積傾印的種類。</span><span class="sxs-lookup"><span data-stu-id="fd425-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="fd425-107">[in]長度`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="fd425-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="fd425-108">如果`dwFlavor`不 DUMP_FLAVOR_Mini，`dwNumItems`應為零。</span><span class="sxs-lookup"><span data-stu-id="fd425-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="fd425-109">[in]陣列[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)執行個體，指定要將小型傾印加入的項目。</span><span class="sxs-lookup"><span data-stu-id="fd425-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="fd425-110">如果`dwFlavor`不 DUMP_FLAVOR_Mini，`items`應為 null。</span><span class="sxs-lookup"><span data-stu-id="fd425-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="fd425-111">[in]保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="fd425-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd425-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="fd425-112">Return Value</span></span>  
  
|<span data-ttu-id="fd425-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd425-113">HRESULT</span></span>|<span data-ttu-id="fd425-114">描述</span><span class="sxs-lookup"><span data-stu-id="fd425-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd425-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd425-115">S_OK</span></span>|<span data-ttu-id="fd425-116">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="fd425-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="fd425-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd425-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd425-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="fd425-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd425-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd425-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd425-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="fd425-120">The call timed out.</span></span>|  
|<span data-ttu-id="fd425-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd425-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd425-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="fd425-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd425-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd425-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd425-124">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="fd425-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd425-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd425-125">E_FAIL</span></span>|<span data-ttu-id="fd425-126">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="fd425-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd425-127">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="fd425-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd425-128">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="fd425-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd425-129">備註</span><span class="sxs-lookup"><span data-stu-id="fd425-129">Remarks</span></span>  
 <span data-ttu-id="fd425-130">`BeginCustomDump`方法設定自訂堆積傾印組態。</span><span class="sxs-lookup"><span data-stu-id="fd425-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="fd425-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)方法清除自訂堆積傾印組態，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="fd425-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="fd425-132">它應該呼叫自訂堆積傾印完成後。</span><span class="sxs-lookup"><span data-stu-id="fd425-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fd425-133">無法呼叫`EndCustomDump`會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="fd425-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd425-134">需求</span><span class="sxs-lookup"><span data-stu-id="fd425-134">Requirements</span></span>  
 <span data-ttu-id="fd425-135">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd425-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd425-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd425-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd425-137">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="fd425-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd425-138">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd425-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd425-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd425-139">See Also</span></span>  
 [<span data-ttu-id="fd425-140">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="fd425-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="fd425-141">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="fd425-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="fd425-142">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="fd425-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
