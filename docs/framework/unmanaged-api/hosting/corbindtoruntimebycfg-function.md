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
ms.openlocfilehash: 3802354bf52cd2aab2a4149d565993b9965e8312
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138292"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="10a65-102">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="10a65-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="10a65-103">使用從 XML 檔案讀取的版本資訊，將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="10a65-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="10a65-104">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="10a65-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a65-105">語法</span><span class="sxs-lookup"><span data-stu-id="10a65-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="10a65-106">參數</span><span class="sxs-lookup"><span data-stu-id="10a65-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="10a65-107">在讀取 XML 檔案之 `IStream` 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="10a65-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="10a65-108">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="10a65-108">[in] Reserved for future use.</span></span> <span data-ttu-id="10a65-109">使用0（零）作為值。</span><span class="sxs-lookup"><span data-stu-id="10a65-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="10a65-110">在[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉的值，指定 CLR 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="10a65-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="10a65-111">在執行[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面之 coclass 的 `CLSID`。</span><span class="sxs-lookup"><span data-stu-id="10a65-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="10a65-112">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="10a65-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="10a65-113">在`ICorRuntimeHost` 或 `ICLRRuntimeHost` 介面的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="10a65-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="10a65-114">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="10a65-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="10a65-115">脫銷傳回之介面位址的指標。</span><span class="sxs-lookup"><span data-stu-id="10a65-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10a65-116">備註</span><span class="sxs-lookup"><span data-stu-id="10a65-116">Remarks</span></span>  
 <span data-ttu-id="10a65-117">XML 檔案的格式會在標準應用程式佈建檔案之後進行模型化。</span><span class="sxs-lookup"><span data-stu-id="10a65-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="10a65-118">如需 XML 檔案的詳細資訊，請參閱[設定檔案架構](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="10a65-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a65-119">需求</span><span class="sxs-lookup"><span data-stu-id="10a65-119">Requirements</span></span>  
 <span data-ttu-id="10a65-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10a65-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10a65-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="10a65-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10a65-122">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="10a65-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10a65-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10a65-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a65-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="10a65-124">See also</span></span>

- [<span data-ttu-id="10a65-125">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="10a65-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="10a65-126">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="10a65-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="10a65-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="10a65-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="10a65-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="10a65-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="10a65-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="10a65-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="10a65-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="10a65-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
