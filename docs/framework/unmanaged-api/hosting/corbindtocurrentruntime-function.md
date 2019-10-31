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
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138324"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="308a5-102">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="308a5-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="308a5-103">使用儲存在 XML 檔案中的版本資訊，將 common language runtime （CLR）載入進程中。</span><span class="sxs-lookup"><span data-stu-id="308a5-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="308a5-104">XML 檔案的格式會在標準應用程式佈建檔案之後進行模型化。</span><span class="sxs-lookup"><span data-stu-id="308a5-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="308a5-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../../../docs/framework/configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="308a5-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="308a5-106">此函式在 .NET Framework 4 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="308a5-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="308a5-107">請參閱將[Common Language Runtime 載入進程中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="308a5-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="308a5-108">語法</span><span class="sxs-lookup"><span data-stu-id="308a5-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="308a5-109">參數</span><span class="sxs-lookup"><span data-stu-id="308a5-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="308a5-110">在應用程式佈建檔的名稱，指定要載入的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="308a5-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="308a5-111">如果檔案名不是完整名稱，則會假設為與呼叫相同的目錄。</span><span class="sxs-lookup"><span data-stu-id="308a5-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="308a5-112">要載入的執行階段版本，是由設定檔的[\<r q >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)元素中的 version 屬性所描述。</span><span class="sxs-lookup"><span data-stu-id="308a5-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="308a5-113">如果未指定任何版本，或找不到 `<requiredRuntime>` 專案，則會載入電腦上所安裝的最新 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="308a5-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="308a5-114">在執行[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面之 coclass 的 `CLSID`。</span><span class="sxs-lookup"><span data-stu-id="308a5-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="308a5-115">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="308a5-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="308a5-116">在您所要求之介面的 `IID`。</span><span class="sxs-lookup"><span data-stu-id="308a5-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="308a5-117">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="308a5-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="308a5-118">脫銷傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="308a5-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="308a5-119">需求</span><span class="sxs-lookup"><span data-stu-id="308a5-119">Requirements</span></span>  
 <span data-ttu-id="308a5-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="308a5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="308a5-121">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="308a5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="308a5-122">連結**庫：** Mscoree.dll .dll</span><span class="sxs-lookup"><span data-stu-id="308a5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="308a5-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="308a5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308a5-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="308a5-124">See also</span></span>

- [<span data-ttu-id="308a5-125">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="308a5-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="308a5-126">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="308a5-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="308a5-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="308a5-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="308a5-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="308a5-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="308a5-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="308a5-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="308a5-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="308a5-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
