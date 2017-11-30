---
title: "CorBindToRuntimeByCfg 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbf5a486246d1fb596c08f1510e6d5d89b03df62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="a4fe7-102">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="a4fe7-103">載入處理序的 common language runtime (CLR) 使用會從 XML 檔案讀取的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="a4fe7-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4fe7-105">語法</span><span class="sxs-lookup"><span data-stu-id="a4fe7-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4fe7-106">參數</span><span class="sxs-lookup"><span data-stu-id="a4fe7-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="a4fe7-107">[in]指標`IStream`讀取 XML 檔案的物件。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="a4fe7-108">[in]保留供未來使用。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-108">[in] Reserved for future use.</span></span> <span data-ttu-id="a4fe7-109">使用 0 （零） 當做值。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a4fe7-110">[in]值為[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉，指定 CLR 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a4fe7-111">[in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a4fe7-112">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a4fe7-113">[in]`IID`的其中一個`ICorRuntimeHost`或`ICLRRuntimeHost`介面。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="a4fe7-114">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a4fe7-115">[out]傳回介面的位址指標。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4fe7-116">備註</span><span class="sxs-lookup"><span data-stu-id="a4fe7-116">Remarks</span></span>  
 <span data-ttu-id="a4fe7-117">XML 檔案的格式被建立的標準應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="a4fe7-118">如需 XML 檔案的詳細資訊，請參閱[組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4fe7-119">需求</span><span class="sxs-lookup"><span data-stu-id="a4fe7-119">Requirements</span></span>  
 <span data-ttu-id="a4fe7-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4fe7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4fe7-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a4fe7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4fe7-122">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a4fe7-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4fe7-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4fe7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4fe7-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4fe7-124">See Also</span></span>  
 [<span data-ttu-id="a4fe7-125">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="a4fe7-126">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="a4fe7-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="a4fe7-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="a4fe7-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="a4fe7-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="a4fe7-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="a4fe7-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
