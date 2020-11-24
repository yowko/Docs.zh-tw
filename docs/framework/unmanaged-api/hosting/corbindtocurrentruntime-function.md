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
ms.openlocfilehash: 4a8ab6e1aeedef5b821fc977387b8039f54edd64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682493"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="f6497-102">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="f6497-102">CorBindToCurrentRuntime Function</span></span>

<span data-ttu-id="f6497-103">使用儲存在 XML 檔案中的版本資訊，將 common language runtime (CLR) 載入至進程。</span><span class="sxs-lookup"><span data-stu-id="f6497-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="f6497-104">XML 檔案的格式是在標準應用程式佈建檔之後進行模型化。</span><span class="sxs-lookup"><span data-stu-id="f6497-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="f6497-105">如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f6497-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="f6497-106">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="f6497-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="f6497-107">請參閱將 [Common Language Runtime 載入至進程](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="f6497-107">See [Loading the Common Language Runtime into a Process](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6497-108">語法</span><span class="sxs-lookup"><span data-stu-id="f6497-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6497-109">參數</span><span class="sxs-lookup"><span data-stu-id="f6497-109">Parameters</span></span>  

 `pwszFileName`  
 <span data-ttu-id="f6497-110">在應用程式佈建檔的名稱，指定要載入的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="f6497-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="f6497-111">如果檔案名不是完整名稱，則會假設該名稱與可執行檔的可執行檔位於相同的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f6497-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="f6497-112">設定檔元素中的 version 屬性會描述要載入的執行階段版本 [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="f6497-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="f6497-113">如果未指定任何版本，或如果找不到專案，則會 `<requiredRuntime>` 載入電腦上所安裝之最新版本的 CLR。</span><span class="sxs-lookup"><span data-stu-id="f6497-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="f6497-114">在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="f6497-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="f6497-115">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="f6497-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="f6497-116">在 `IID` 您所要求之介面的。</span><span class="sxs-lookup"><span data-stu-id="f6497-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="f6497-117">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="f6497-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="f6497-118">擴展傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="f6497-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6497-119">需求</span><span class="sxs-lookup"><span data-stu-id="f6497-119">Requirements</span></span>  

 <span data-ttu-id="f6497-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f6497-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6497-121">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f6497-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6497-122">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6497-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6497-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6497-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6497-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6497-124">See also</span></span>

- [<span data-ttu-id="f6497-125">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="f6497-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="f6497-126">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="f6497-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="f6497-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="f6497-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="f6497-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="f6497-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="f6497-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="f6497-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="f6497-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="f6497-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
