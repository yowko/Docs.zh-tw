---
title: CorBindToRuntimeByCfg 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178237"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="d2a9b-102">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="d2a9b-103">通過使用從 XML 檔讀取的版本資訊將通用語言運行時 （CLR） 載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="d2a9b-104">此功能已在 .NET 框架 4 中棄用。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a9b-105">語法</span><span class="sxs-lookup"><span data-stu-id="d2a9b-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2a9b-106">參數</span><span class="sxs-lookup"><span data-stu-id="d2a9b-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="d2a9b-107">[在]指向讀取 XML`IStream`檔的物件的指標。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="d2a9b-108">[在]保留以供將來使用。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-108">[in] Reserved for future use.</span></span> <span data-ttu-id="d2a9b-109">使用 0（零）作為值。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="d2a9b-110">[在]指定 CLR 的啟動行為的[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉的值。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="d2a9b-111">[在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="d2a9b-112">支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="d2a9b-113">[在]或`IID``ICorRuntimeHost`介面 的`ICLRRuntimeHost`。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="d2a9b-114">支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="d2a9b-115">[出]指向返回介面位址的指標。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2a9b-116">備註</span><span class="sxs-lookup"><span data-stu-id="d2a9b-116">Remarks</span></span>  
 <span data-ttu-id="d2a9b-117">XML 檔的格式以標準應用程式佈建檔建模。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="d2a9b-118">有關 XML 檔的詳細資訊，請參閱[設定檔架構](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2a9b-119">需求</span><span class="sxs-lookup"><span data-stu-id="d2a9b-119">Requirements</span></span>  
 <span data-ttu-id="d2a9b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2a9b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a9b-121">**標題：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d2a9b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d2a9b-122">**庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2a9b-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d2a9b-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a9b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a9b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2a9b-124">See also</span></span>

- [<span data-ttu-id="d2a9b-125">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="d2a9b-126">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="d2a9b-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="d2a9b-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="d2a9b-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="d2a9b-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="d2a9b-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d2a9b-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
