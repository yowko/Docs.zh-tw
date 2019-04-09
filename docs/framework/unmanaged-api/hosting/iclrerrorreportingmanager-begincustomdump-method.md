---
title: ICLRErrorReportingManager::BeginCustomDump 方法
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cb6cd8d31e01ea2f1749a6cb4d17173679f0c06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104106"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="0cbfa-102">ICLRErrorReportingManager::BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="0cbfa-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="0cbfa-103">指定錯誤報告的自訂堆積傾印的組態。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cbfa-104">語法</span><span class="sxs-lookup"><span data-stu-id="0cbfa-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cbfa-105">參數</span><span class="sxs-lookup"><span data-stu-id="0cbfa-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="0cbfa-106">[in]A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)值，指出來建置自訂的堆積傾印的堆積傾印的種類。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="0cbfa-107">[in]長度`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="0cbfa-108">如果`dwFlavor`不是 DUMP_FLAVOR_Mini，`dwNumItems`應為零。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="0cbfa-109">[in]陣列[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)執行個體，指定要加入 小型傾印的項目。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="0cbfa-110">如果`dwFlavor`不是 DUMP_FLAVOR_Mini，`items`應為 null。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="0cbfa-111">[in]Reserved for future use.</span><span class="sxs-lookup"><span data-stu-id="0cbfa-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cbfa-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="0cbfa-112">Return Value</span></span>  
  
|<span data-ttu-id="0cbfa-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cbfa-113">HRESULT</span></span>|<span data-ttu-id="0cbfa-114">描述</span><span class="sxs-lookup"><span data-stu-id="0cbfa-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cbfa-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cbfa-115">S_OK</span></span>|<span data-ttu-id="0cbfa-116">此方法傳回成功。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="0cbfa-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0cbfa-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0cbfa-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0cbfa-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0cbfa-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0cbfa-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-120">The call timed out.</span></span>|  
|<span data-ttu-id="0cbfa-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0cbfa-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0cbfa-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0cbfa-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0cbfa-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0cbfa-124">事件已取消時已封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0cbfa-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cbfa-125">E_FAIL</span></span>|<span data-ttu-id="0cbfa-126">發生未知的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0cbfa-127">方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0cbfa-128">若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cbfa-129">備註</span><span class="sxs-lookup"><span data-stu-id="0cbfa-129">Remarks</span></span>  
 <span data-ttu-id="0cbfa-130">`BeginCustomDump`方法會設定自訂的堆積傾印組態。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="0cbfa-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)方法會清除自訂的堆積傾印組態，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="0cbfa-132">自訂的堆積傾印完成之後，應該會呼叫它。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0cbfa-133">無法呼叫`EndCustomDump`會造成記憶體遺漏。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cbfa-134">需求</span><span class="sxs-lookup"><span data-stu-id="0cbfa-134">Requirements</span></span>  
 <span data-ttu-id="0cbfa-135">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cbfa-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cbfa-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0cbfa-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0cbfa-137">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="0cbfa-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0cbfa-138">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="0cbfa-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0cbfa-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cbfa-139">See also</span></span>

- [<span data-ttu-id="0cbfa-140">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="0cbfa-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="0cbfa-141">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="0cbfa-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="0cbfa-142">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="0cbfa-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
