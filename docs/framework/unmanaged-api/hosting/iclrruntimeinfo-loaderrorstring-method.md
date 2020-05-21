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
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762184"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="182de-102">ICLRRuntimeInfo::LoadErrorString 方法</span><span class="sxs-lookup"><span data-stu-id="182de-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="182de-103">針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="182de-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="182de-104">這個方法會取代下列函數：</span><span class="sxs-lookup"><span data-stu-id="182de-104">This method supersedes the following functions:</span></span>  
  
- [<span data-ttu-id="182de-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="182de-105">LoadStringRC</span></span>](loadstringrc-function.md)  
  
- [<span data-ttu-id="182de-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="182de-106">LoadStringRCEx</span></span>](loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="182de-107">語法</span><span class="sxs-lookup"><span data-stu-id="182de-107">Syntax</span></span>  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="182de-108">參數</span><span class="sxs-lookup"><span data-stu-id="182de-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="182de-109">在要轉譯的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="182de-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="182de-110">脫銷與指定之 HRESULT 相關聯的訊息字串。</span><span class="sxs-lookup"><span data-stu-id="182de-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="182de-111">[in、out]`pwzbuffer`要避免緩衝區溢位的大小。</span><span class="sxs-lookup"><span data-stu-id="182de-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="182de-112">如果 `pwzbuffer` 為 null， `pcchBuffer` 則會提供的預期大小 `pwzbuffer` 以允許預先配置。</span><span class="sxs-lookup"><span data-stu-id="182de-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="182de-113">在文化特性識別碼。</span><span class="sxs-lookup"><span data-stu-id="182de-113">[in] The culture identifier.</span></span> <span data-ttu-id="182de-114">若要使用預設文化特性，您必須指定-1。</span><span class="sxs-lookup"><span data-stu-id="182de-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="182de-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="182de-115">Return Value</span></span>  
 <span data-ttu-id="182de-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="182de-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="182de-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="182de-117">HRESULT</span></span>|<span data-ttu-id="182de-118">Description</span><span class="sxs-lookup"><span data-stu-id="182de-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="182de-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="182de-119">S_OK</span></span>|<span data-ttu-id="182de-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="182de-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="182de-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="182de-121">E_POINTER</span></span>|<span data-ttu-id="182de-122">`pcchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="182de-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="182de-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="182de-123">E_INVALIDARG</span></span>|<span data-ttu-id="182de-124">`pwzBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="182de-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="182de-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="182de-125">Requirements</span></span>  
 <span data-ttu-id="182de-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="182de-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="182de-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="182de-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="182de-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="182de-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="182de-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="182de-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182de-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="182de-130">See also</span></span>

- [<span data-ttu-id="182de-131">ICLRRuntimeInfo 介面</span><span class="sxs-lookup"><span data-stu-id="182de-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="182de-132">裝載介面</span><span class="sxs-lookup"><span data-stu-id="182de-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="182de-133">裝載</span><span class="sxs-lookup"><span data-stu-id="182de-133">Hosting</span></span>](index.md)
