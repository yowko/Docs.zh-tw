---
title: "ICLRRuntimeInfo::LoadErrorString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="73dab-102">ICLRRuntimeInfo::LoadErrorString 方法</span><span class="sxs-lookup"><span data-stu-id="73dab-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="73dab-103">HRESULT 值轉譯為適當的錯誤訊息指定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="73dab-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="73dab-104">這個方法會取代以下函數：</span><span class="sxs-lookup"><span data-stu-id="73dab-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="73dab-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="73dab-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="73dab-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="73dab-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="73dab-107">語法</span><span class="sxs-lookup"><span data-stu-id="73dab-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73dab-108">參數</span><span class="sxs-lookup"><span data-stu-id="73dab-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="73dab-109">[in]若要翻譯 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="73dab-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="73dab-110">[out]指定的 HRESULT 相關聯的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="73dab-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="73dab-111">[in、 out]大小`pwzbuffer`以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="73dab-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="73dab-112">如果`pwzbuffer`為 null，`pcchBuffer`提供的預期的大小`pwzbuffer`允許 preallocation。</span><span class="sxs-lookup"><span data-stu-id="73dab-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="73dab-113">[in]文化特性識別項。</span><span class="sxs-lookup"><span data-stu-id="73dab-113">[in] The culture identifier.</span></span> <span data-ttu-id="73dab-114">若要使用的預設文化特性，您必須指定-1。</span><span class="sxs-lookup"><span data-stu-id="73dab-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73dab-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="73dab-115">Return Value</span></span>  
 <span data-ttu-id="73dab-116">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="73dab-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73dab-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73dab-117">HRESULT</span></span>|<span data-ttu-id="73dab-118">描述</span><span class="sxs-lookup"><span data-stu-id="73dab-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73dab-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="73dab-119">S_OK</span></span>|<span data-ttu-id="73dab-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="73dab-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="73dab-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="73dab-121">E_POINTER</span></span>|<span data-ttu-id="73dab-122">`pcchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="73dab-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="73dab-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73dab-123">E_INVALIDARG</span></span>|<span data-ttu-id="73dab-124">`pwzBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="73dab-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73dab-125">需求</span><span class="sxs-lookup"><span data-stu-id="73dab-125">Requirements</span></span>  
 <span data-ttu-id="73dab-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="73dab-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73dab-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="73dab-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="73dab-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="73dab-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73dab-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73dab-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73dab-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73dab-130">See Also</span></span>  
 [<span data-ttu-id="73dab-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="73dab-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="73dab-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="73dab-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="73dab-133">裝載</span><span class="sxs-lookup"><span data-stu-id="73dab-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
