---
title: "CorBindToCurrentRuntime 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fed8829f8f14833724d1770273ff905d6f5eabf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="b4062-102">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="b4062-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="b4062-103">載入處理序的 common language runtime (CLR) 使用 XML 檔案中儲存的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="b4062-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="b4062-104">XML 檔案的格式被建立的標準應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="b4062-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="b4062-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b4062-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="b4062-106">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b4062-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="b4062-107">請參閱[載入處理序的 Common Language Runtime](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f)。</span><span class="sxs-lookup"><span data-stu-id="b4062-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4062-108">語法</span><span class="sxs-lookup"><span data-stu-id="b4062-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4062-109">參數</span><span class="sxs-lookup"><span data-stu-id="b4062-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="b4062-110">[in]指定的版本載入 CLR 應用程式組態檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4062-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="b4062-111">如果檔案名稱的格式不完整，則會假設位於相同目錄中進行呼叫的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="b4062-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="b4062-112">Version 屬性中所描述要載入的執行階段版本[ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)組態檔元素。</span><span class="sxs-lookup"><span data-stu-id="b4062-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="b4062-113">如果未指定版本，或如果`<requiredRuntime>`找不到項目，最新版本的電腦上已安裝的 clr 載入。</span><span class="sxs-lookup"><span data-stu-id="b4062-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="b4062-114">[in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="b4062-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="b4062-115">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="b4062-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="b4062-116">[in]`IID`您要求的介面。</span><span class="sxs-lookup"><span data-stu-id="b4062-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="b4062-117">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="b4062-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="b4062-118">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b4062-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4062-119">需求</span><span class="sxs-lookup"><span data-stu-id="b4062-119">Requirements</span></span>  
 <span data-ttu-id="b4062-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4062-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4062-121">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4062-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4062-122">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4062-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4062-123">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4062-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4062-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4062-124">See Also</span></span>  
 [<span data-ttu-id="b4062-125">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="b4062-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="b4062-126">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="b4062-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="b4062-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="b4062-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="b4062-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="b4062-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="b4062-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="b4062-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="b4062-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="b4062-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
