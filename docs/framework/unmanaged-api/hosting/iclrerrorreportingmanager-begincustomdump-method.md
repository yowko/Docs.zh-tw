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
ms.openlocfilehash: b5d58a90901b7d7cb80ea7f25401b857b4d4875e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434508"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="1d2fc-102">ICLRErrorReportingManager::BeginCustomDump 方法</span><span class="sxs-lookup"><span data-stu-id="1d2fc-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="1d2fc-103">指定錯誤報告的自訂堆積傾印的組態。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d2fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="1d2fc-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d2fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="1d2fc-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="1d2fc-106">[in]A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)值，指出在其上建置自訂堆積傾印堆積傾印的種類。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="1d2fc-107">[in]長度`items`陣列。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="1d2fc-108">如果`dwFlavor`不 DUMP_FLAVOR_Mini，`dwNumItems`應為零。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="1d2fc-109">[in]陣列[CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)執行個體，指定要將小型傾印加入的項目。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="1d2fc-110">如果`dwFlavor`不 DUMP_FLAVOR_Mini，`items`應為 null。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="1d2fc-111">[in]保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d2fc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="1d2fc-112">Return Value</span></span>  
  
|<span data-ttu-id="1d2fc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d2fc-113">HRESULT</span></span>|<span data-ttu-id="1d2fc-114">描述</span><span class="sxs-lookup"><span data-stu-id="1d2fc-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d2fc-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d2fc-115">S_OK</span></span>|<span data-ttu-id="1d2fc-116">方法成功傳回。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="1d2fc-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d2fc-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d2fc-118">Common language runtime (CLR) 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d2fc-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d2fc-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d2fc-120">呼叫已逾時。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-120">The call timed out.</span></span>|  
|<span data-ttu-id="1d2fc-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d2fc-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d2fc-122">呼叫端未擁有鎖定。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d2fc-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d2fc-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d2fc-124">事件已取消時封鎖的執行緒或 fiber 等候它。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d2fc-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d2fc-125">E_FAIL</span></span>|<span data-ttu-id="1d2fc-126">發生未知的嚴重失敗。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d2fc-127">方法會傳回 E_FAIL 之後，CLR 就不再可用的處理序內。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d2fc-128">裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d2fc-129">備註</span><span class="sxs-lookup"><span data-stu-id="1d2fc-129">Remarks</span></span>  
 <span data-ttu-id="1d2fc-130">`BeginCustomDump`方法設定自訂堆積傾印組態。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="1d2fc-131">[EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)方法清除自訂堆積傾印組態，並釋放任何相關聯的狀態。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="1d2fc-132">它應該呼叫自訂堆積傾印完成後。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d2fc-133">無法呼叫`EndCustomDump`會導致記憶體流失。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d2fc-134">需求</span><span class="sxs-lookup"><span data-stu-id="1d2fc-134">Requirements</span></span>  
 <span data-ttu-id="1d2fc-135">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d2fc-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d2fc-136">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d2fc-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d2fc-137">**程式庫：** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1d2fc-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d2fc-138">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d2fc-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d2fc-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1d2fc-139">See Also</span></span>  
 [<span data-ttu-id="1d2fc-140">CustomDumpItem 結構</span><span class="sxs-lookup"><span data-stu-id="1d2fc-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="1d2fc-141">ECustomDumpFlavor 列舉</span><span class="sxs-lookup"><span data-stu-id="1d2fc-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="1d2fc-142">ICLRErrorReportingManager 介面</span><span class="sxs-lookup"><span data-stu-id="1d2fc-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
