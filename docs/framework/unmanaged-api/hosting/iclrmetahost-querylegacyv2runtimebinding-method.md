---
title: "ICLRMetaHost::QueryLegacyV2RuntimeBinding 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.RequestRuntimeLoadedNotification
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c273a1690828e37c8f7fcf5071e42e5bb2c58228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a><span data-ttu-id="1062f-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding 方法</span><span class="sxs-lookup"><span data-stu-id="1062f-102">ICLRMetaHost::QueryLegacyV2RuntimeBinding Method</span></span>
<span data-ttu-id="1062f-103">傳回代表執行階段的舊版啟用原則已繫結，例如，使用的介面`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔項目，直接使用舊版啟用應用程式開發介面，或藉由呼叫[iclrruntimeinfo:: Bindaslegacyv2runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1062f-103">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1062f-104">語法</span><span class="sxs-lookup"><span data-stu-id="1062f-104">Syntax</span></span>  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1062f-105">參數</span><span class="sxs-lookup"><span data-stu-id="1062f-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="1062f-106">[in]此參數唯一有效的值是的 Required.Currently `IID_ICLRRuntimeInfo`。</span><span class="sxs-lookup"><span data-stu-id="1062f-106">[in] Required.Currently the only valid value for this parameter is `IID_ICLRRuntimeInfo`.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="1062f-107">[out] 必要項。</span><span class="sxs-lookup"><span data-stu-id="1062f-107">[out] Required.</span></span> <span data-ttu-id="1062f-108">此方法傳回時，包含指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)表示已繫結到舊版啟用原則的執行階段介面。</span><span class="sxs-lookup"><span data-stu-id="1062f-108">When this method returns, contains a pointer to the [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface that represents a runtime that has been bound to legacy activation policy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1062f-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="1062f-109">Return Value</span></span>  
 <span data-ttu-id="1062f-110">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="1062f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="1062f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1062f-111">HRESULT</span></span>|<span data-ttu-id="1062f-112">描述</span><span class="sxs-lookup"><span data-stu-id="1062f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1062f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="1062f-113">S_OK</span></span>|<span data-ttu-id="1062f-114">這個方法順利完成，且傳回已繫結到舊版啟用原則的執行階段。</span><span class="sxs-lookup"><span data-stu-id="1062f-114">The method completed successfully and returned a runtime that was bound to legacy activation policy.</span></span>|  
|<span data-ttu-id="1062f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1062f-115">S_FALSE</span></span>|<span data-ttu-id="1062f-116">這個方法順利完成，但是尚未已繫結舊版執行階段。</span><span class="sxs-lookup"><span data-stu-id="1062f-116">The method completed successfully, but a legacy runtime has not yet been bound.</span></span>|  
|<span data-ttu-id="1062f-117">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="1062f-117">E_NOINTERFACE</span></span>|<span data-ttu-id="1062f-118">此方法找到的執行階段已繫結到舊版啟用原則，但該執行階段不支援 `riid`。</span><span class="sxs-lookup"><span data-stu-id="1062f-118">The method found a runtime that was bound to legacy activation policy, but `riid` is not supported by that runtime.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1062f-119">備註</span><span class="sxs-lookup"><span data-stu-id="1062f-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1062f-120">需求</span><span class="sxs-lookup"><span data-stu-id="1062f-120">Requirements</span></span>  
 <span data-ttu-id="1062f-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1062f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1062f-122">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1062f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1062f-123">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1062f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1062f-124">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1062f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1062f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1062f-125">See Also</span></span>  
 [<span data-ttu-id="1062f-126">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="1062f-126">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="1062f-127">裝載</span><span class="sxs-lookup"><span data-stu-id="1062f-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
