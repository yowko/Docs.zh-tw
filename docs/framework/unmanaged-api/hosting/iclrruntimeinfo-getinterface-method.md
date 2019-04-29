---
title: ICLRRuntimeInfo::GetInterface 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f229e421cc69f2ff45110233c4c6c36d7a1fc4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771757"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="1c455-102">ICLRRuntimeInfo::GetInterface 方法</span><span class="sxs-lookup"><span data-stu-id="1c455-102">ICLRRuntimeInfo::GetInterface Method</span></span>
<span data-ttu-id="1c455-103">將 CLR 載入目前的處理序，並傳回執行階段介面指標，例如[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)， [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)，並[IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="1c455-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md), and [IMetaDataDispenserEx](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="1c455-104">這個方法會取代所有`CorBindTo`\* 中的函式[已被取代 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)一節。</span><span class="sxs-lookup"><span data-stu-id="1c455-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c455-105">語法</span><span class="sxs-lookup"><span data-stu-id="1c455-105">Syntax</span></span>  
  
```  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c455-106">參數</span><span class="sxs-lookup"><span data-stu-id="1c455-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="1c455-107">[in]Coclass 的 CLSID 的介面。</span><span class="sxs-lookup"><span data-stu-id="1c455-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="1c455-108">[in]要求 IID`rclsid`介面。</span><span class="sxs-lookup"><span data-stu-id="1c455-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="1c455-109">[out]查詢介面的指標。</span><span class="sxs-lookup"><span data-stu-id="1c455-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c455-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1c455-110">Return Value</span></span>  
 <span data-ttu-id="1c455-111">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="1c455-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1c455-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c455-112">HRESULT</span></span>|<span data-ttu-id="1c455-113">描述</span><span class="sxs-lookup"><span data-stu-id="1c455-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c455-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c455-114">S_OK</span></span>|<span data-ttu-id="1c455-115">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="1c455-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="1c455-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="1c455-116">E_POINTER</span></span>|<span data-ttu-id="1c455-117">`ppUnk` 為 null。</span><span class="sxs-lookup"><span data-stu-id="1c455-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="1c455-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1c455-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1c455-119">沒有足夠的記憶體是可用來處理要求。</span><span class="sxs-lookup"><span data-stu-id="1c455-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="1c455-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="1c455-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="1c455-121">不同的執行階段已經繫結到舊版的 CLR 版本 2 的啟用原則。</span><span class="sxs-lookup"><span data-stu-id="1c455-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c455-122">備註</span><span class="sxs-lookup"><span data-stu-id="1c455-122">Remarks</span></span>  
 <span data-ttu-id="1c455-123">這個方法會導致 CLR 載入，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="1c455-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="1c455-124">下表顯示支援的組合，如`rclsid`和`riid`。</span><span class="sxs-lookup"><span data-stu-id="1c455-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="1c455-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="1c455-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="1c455-126">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="1c455-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="1c455-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="1c455-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="1c455-128">IID_IMetaDataDispenser IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="1c455-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="1c455-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1c455-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="1c455-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1c455-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="1c455-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1c455-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="1c455-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="1c455-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="1c455-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="1c455-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="1c455-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="1c455-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="1c455-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="1c455-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="1c455-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="1c455-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="1c455-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="1c455-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="1c455-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="1c455-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1c455-139">需求</span><span class="sxs-lookup"><span data-stu-id="1c455-139">Requirements</span></span>  
 <span data-ttu-id="1c455-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c455-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c455-141">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1c455-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1c455-142">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1c455-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c455-143">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c455-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c455-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c455-144">See also</span></span>

- [<span data-ttu-id="1c455-145">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="1c455-145">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="1c455-146">裝載介面</span><span class="sxs-lookup"><span data-stu-id="1c455-146">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="1c455-147">裝載</span><span class="sxs-lookup"><span data-stu-id="1c455-147">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
