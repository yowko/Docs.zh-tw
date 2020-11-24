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
ms.openlocfilehash: d319382b577844a804c3e4562676491a15de5f63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673770"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="0d761-102">CorBindToRuntimeByCfg 函式</span><span class="sxs-lookup"><span data-stu-id="0d761-102">CorBindToRuntimeByCfg Function</span></span>

<span data-ttu-id="0d761-103">使用從 XML 檔案讀取的版本資訊，將 common language runtime (CLR) 載入處理常式。</span><span class="sxs-lookup"><span data-stu-id="0d761-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="0d761-104">此函式已在 .NET Framework 4 中被取代。</span><span class="sxs-lookup"><span data-stu-id="0d761-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d761-105">語法</span><span class="sxs-lookup"><span data-stu-id="0d761-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0d761-106">參數</span><span class="sxs-lookup"><span data-stu-id="0d761-106">Parameters</span></span>  

 `pCfgStream`  
 <span data-ttu-id="0d761-107">在 `IStream` 物件的指標，該物件會讀取 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d761-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="0d761-108">在保留供日後使用。</span><span class="sxs-lookup"><span data-stu-id="0d761-108">[in] Reserved for future use.</span></span> <span data-ttu-id="0d761-109">使用 0 (零) 作為值。</span><span class="sxs-lookup"><span data-stu-id="0d761-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="0d761-110">在 [STARTUP_FLAGS](startup-flags-enumeration.md) 列舉值，指定 CLR 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="0d761-110">[in] A value of the [STARTUP_FLAGS](startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0d761-111">在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="0d761-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0d761-112">支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="0d761-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0d761-113">在 `IID` `ICorRuntimeHost` 或 `ICLRRuntimeHost` 介面的。</span><span class="sxs-lookup"><span data-stu-id="0d761-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="0d761-114">支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。</span><span class="sxs-lookup"><span data-stu-id="0d761-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0d761-115">擴展傳回之介面的位址指標。</span><span class="sxs-lookup"><span data-stu-id="0d761-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d761-116">備註</span><span class="sxs-lookup"><span data-stu-id="0d761-116">Remarks</span></span>  

 <span data-ttu-id="0d761-117">XML 檔案的格式是在標準應用程式佈建檔之後進行模型化。</span><span class="sxs-lookup"><span data-stu-id="0d761-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="0d761-118">如需 XML 檔案的詳細資訊，請參閱 [設定檔案架構](../../configure-apps/file-schema/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0d761-118">For more information about XML files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d761-119">需求</span><span class="sxs-lookup"><span data-stu-id="0d761-119">Requirements</span></span>  

 <span data-ttu-id="0d761-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d761-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d761-121">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0d761-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d761-122">連結 **庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d761-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d761-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d761-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d761-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d761-124">See also</span></span>

- [<span data-ttu-id="0d761-125">CorBindToCurrentRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="0d761-125">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="0d761-126">CorBindToRuntime 函式</span><span class="sxs-lookup"><span data-stu-id="0d761-126">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="0d761-127">CorBindToRuntimeEx 函式</span><span class="sxs-lookup"><span data-stu-id="0d761-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="0d761-128">CorBindToRuntimeHost 函式</span><span class="sxs-lookup"><span data-stu-id="0d761-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="0d761-129">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="0d761-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="0d761-130">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="0d761-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
