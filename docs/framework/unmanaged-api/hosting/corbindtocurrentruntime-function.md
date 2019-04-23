---
title: CorBindToCurrentRuntime 函式
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0acb322fa3348f0bb2d819529a370110580343c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178057"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="e18c6-102">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="e18c6-103">載入處理序的 common language runtime (CLR) 使用的 XML 檔案中儲存的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="e18c6-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="e18c6-104">XML 檔案的格式被仿造自標準的應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="e18c6-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="e18c6-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e18c6-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="e18c6-106">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e18c6-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="e18c6-107">請參閱[Common Language Runtime 載入處理序](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="e18c6-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e18c6-108">語法</span><span class="sxs-lookup"><span data-stu-id="e18c6-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e18c6-109">參數</span><span class="sxs-lookup"><span data-stu-id="e18c6-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="e18c6-110">[in]指定要載入的 clr 版本的應用程式組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="e18c6-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="e18c6-111">如果檔案名稱的格式不完整，則會假設是在進行呼叫的可執行檔相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e18c6-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="e18c6-112">Version 屬性中所描述要載入的執行階段版本[ \<Requiredruntime> >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)組態檔的項目。</span><span class="sxs-lookup"><span data-stu-id="e18c6-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="e18c6-113">如果未指定版本，或如果`<requiredRuntime>`找不到項目，會載入最新的版本安裝在電腦上的 clr。</span><span class="sxs-lookup"><span data-stu-id="e18c6-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="e18c6-114">[in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e18c6-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="e18c6-115">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="e18c6-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="e18c6-116">[in]`IID`您所要求的介面。</span><span class="sxs-lookup"><span data-stu-id="e18c6-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="e18c6-117">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="e18c6-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="e18c6-118">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e18c6-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e18c6-119">需求</span><span class="sxs-lookup"><span data-stu-id="e18c6-119">Requirements</span></span>  
 <span data-ttu-id="e18c6-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e18c6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e18c6-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e18c6-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e18c6-122">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e18c6-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e18c6-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e18c6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18c6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e18c6-124">See also</span></span>

- [<span data-ttu-id="e18c6-125">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="e18c6-126">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="e18c6-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="e18c6-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="e18c6-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e18c6-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="e18c6-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="e18c6-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
