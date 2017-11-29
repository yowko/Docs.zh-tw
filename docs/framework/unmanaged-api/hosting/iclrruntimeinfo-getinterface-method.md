---
title: "ICLRRuntimeInfo::GetInterface 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0049b4e60f803fbc9ec64e7f20273b1d5729e67f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="23355-102">ICLRRuntimeInfo::GetInterface 方法</span><span class="sxs-lookup"><span data-stu-id="23355-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="23355-103">CLR 載入目前的處理序，並傳回執行階段介面指標，例如[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)， [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)，和[IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="23355-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="23355-104">這個方法會取代所有`CorBindTo`* 函式的[已被取代的 CLR 裝載函數](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="23355-104">This method supersedes all the `CorBindTo`* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23355-105">語法</span><span class="sxs-lookup"><span data-stu-id="23355-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23355-106">參數</span><span class="sxs-lookup"><span data-stu-id="23355-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="23355-107">[in]Coclass CLSID 介面。</span><span class="sxs-lookup"><span data-stu-id="23355-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="23355-108">[in]所要求的 IID`rclsid`介面。</span><span class="sxs-lookup"><span data-stu-id="23355-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="23355-109">[out]查詢介面的指標。</span><span class="sxs-lookup"><span data-stu-id="23355-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23355-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="23355-110">Return Value</span></span>  
 <span data-ttu-id="23355-111">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="23355-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="23355-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="23355-112">HRESULT</span></span>|<span data-ttu-id="23355-113">描述</span><span class="sxs-lookup"><span data-stu-id="23355-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="23355-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="23355-114">S_OK</span></span>|<span data-ttu-id="23355-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="23355-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="23355-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="23355-116">E_POINTER</span></span>|<span data-ttu-id="23355-117">`ppUnk` 為 null。</span><span class="sxs-lookup"><span data-stu-id="23355-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="23355-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="23355-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="23355-119">沒有足夠的記憶體是可用來處理要求。</span><span class="sxs-lookup"><span data-stu-id="23355-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="23355-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="23355-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="23355-121">不同的執行階段已經繫結到舊版的 CLR 版本 2 的啟用原則。</span><span class="sxs-lookup"><span data-stu-id="23355-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23355-122">備註</span><span class="sxs-lookup"><span data-stu-id="23355-122">Remarks</span></span>  
 <span data-ttu-id="23355-123">這個方法會導致 CLR 載入，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="23355-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="23355-124">下表顯示支援的組合`rclsid`和`riid`。</span><span class="sxs-lookup"><span data-stu-id="23355-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="23355-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="23355-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="23355-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="23355-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="23355-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="23355-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="23355-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="23355-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="23355-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23355-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="23355-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23355-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="23355-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23355-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="23355-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="23355-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="23355-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="23355-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="23355-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="23355-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="23355-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="23355-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="23355-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="23355-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="23355-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="23355-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="23355-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="23355-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="23355-139">需求</span><span class="sxs-lookup"><span data-stu-id="23355-139">Requirements</span></span>  
 <span data-ttu-id="23355-140">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="23355-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23355-141">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="23355-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="23355-142">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="23355-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23355-143">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23355-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23355-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23355-144">See Also</span></span>  
 [<span data-ttu-id="23355-145">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="23355-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="23355-146">裝載介面</span><span class="sxs-lookup"><span data-stu-id="23355-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="23355-147">裝載</span><span class="sxs-lookup"><span data-stu-id="23355-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
