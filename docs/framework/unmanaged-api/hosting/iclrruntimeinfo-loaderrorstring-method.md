---
title: ICLRRuntimeInfo::LoadErrorString 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b485811b0e7d2f657ff2d2c1d7a2aa135e48a335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154683"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="86d7d-102">ICLRRuntimeInfo::LoadErrorString 方法</span><span class="sxs-lookup"><span data-stu-id="86d7d-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="86d7d-103">將 HRESULT 值轉譯成適當的錯誤訊息指定的文化特性。</span><span class="sxs-lookup"><span data-stu-id="86d7d-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="86d7d-104">這個方法會取代以下函數：</span><span class="sxs-lookup"><span data-stu-id="86d7d-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="86d7d-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="86d7d-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="86d7d-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="86d7d-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="86d7d-107">語法</span><span class="sxs-lookup"><span data-stu-id="86d7d-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d7d-108">參數</span><span class="sxs-lookup"><span data-stu-id="86d7d-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="86d7d-109">[in]若要翻譯 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="86d7d-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="86d7d-110">[out]指定的 HRESULT 相關聯的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="86d7d-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="86d7d-111">[in、 out]大小`pwzbuffer`以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="86d7d-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="86d7d-112">如果`pwzbuffer`為 null，`pcchBuffer`提供的預期的大小`pwzbuffer`以便預先配置。</span><span class="sxs-lookup"><span data-stu-id="86d7d-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="86d7d-113">[in]文化特性識別項。</span><span class="sxs-lookup"><span data-stu-id="86d7d-113">[in] The culture identifier.</span></span> <span data-ttu-id="86d7d-114">若要使用的預設文化特性，您必須指定-1。</span><span class="sxs-lookup"><span data-stu-id="86d7d-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86d7d-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="86d7d-115">Return Value</span></span>  
 <span data-ttu-id="86d7d-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="86d7d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="86d7d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86d7d-117">HRESULT</span></span>|<span data-ttu-id="86d7d-118">描述</span><span class="sxs-lookup"><span data-stu-id="86d7d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86d7d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="86d7d-119">S_OK</span></span>|<span data-ttu-id="86d7d-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="86d7d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="86d7d-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="86d7d-121">E_POINTER</span></span>|<span data-ttu-id="86d7d-122">`pcchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="86d7d-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="86d7d-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="86d7d-123">E_INVALIDARG</span></span>|<span data-ttu-id="86d7d-124">`pwzBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="86d7d-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86d7d-125">需求</span><span class="sxs-lookup"><span data-stu-id="86d7d-125">Requirements</span></span>  
 <span data-ttu-id="86d7d-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86d7d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d7d-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="86d7d-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="86d7d-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="86d7d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86d7d-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d7d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d7d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86d7d-130">See also</span></span>

- [<span data-ttu-id="86d7d-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="86d7d-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="86d7d-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="86d7d-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="86d7d-133">裝載</span><span class="sxs-lookup"><span data-stu-id="86d7d-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
