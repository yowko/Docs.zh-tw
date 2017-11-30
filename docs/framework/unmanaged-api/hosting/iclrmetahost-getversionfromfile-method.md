---
title: "ICLRMetaHost::GetVersionFromFile 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetaHost.GetVersionFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90fcf5ca8306c4e91ff6b96bac36ad2639d81d5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="6f4e1-102">ICLRMetaHost::GetVersionFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="6f4e1-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="6f4e1-103">取得組件的原始.NET Framework 編譯版本 （儲存於中繼資料），指定其檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="6f4e1-104">這個方法會取代[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-104">This method supersedes the [GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f4e1-105">語法</span><span class="sxs-lookup"><span data-stu-id="6f4e1-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f4e1-106">參數</span><span class="sxs-lookup"><span data-stu-id="6f4e1-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="6f4e1-107">[in]完整的組件檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="6f4e1-108">[out].NET Framework 編譯版本儲存在中繼資料，以格式"v*A*。*B*[。*X*]"。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="6f4e1-109">*A*， *B*，和*X*是對應至主要版本、 次要版本和組建編號的十進位數字。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="6f4e1-110">這個字串的長度僅限於 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f4e1-111">此輸出符合.NET Framework 版本的目錄名稱 C:\Windows\Microsoft.NET\Framework 底下所顯示的樣子。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="6f4e1-112">範例值是"v1.0.3705"、"v1.1.4322"、"v2.0.50727，"和"v4.0。*X*"，其中*X*取決於已安裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="6f4e1-113">請注意，"v"前置詞。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="6f4e1-114">[in、 out]大小`pwzbuffer`以避免緩衝區滿溢。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f4e1-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f4e1-115">Return Value</span></span>  
 <span data-ttu-id="6f4e1-116">這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6f4e1-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6f4e1-117">HRESULT</span></span>|<span data-ttu-id="6f4e1-118">描述</span><span class="sxs-lookup"><span data-stu-id="6f4e1-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6f4e1-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="6f4e1-119">S_OK</span></span>|<span data-ttu-id="6f4e1-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="6f4e1-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="6f4e1-121">E_POINTER</span></span>|<span data-ttu-id="6f4e1-122">`pwzbuffer` 或 `pcchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="6f4e1-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="6f4e1-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="6f4e1-124">緩衝區是太小。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f4e1-125">需求</span><span class="sxs-lookup"><span data-stu-id="6f4e1-125">Requirements</span></span>  
 <span data-ttu-id="6f4e1-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f4e1-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f4e1-127">**標頭：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6f4e1-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f4e1-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6f4e1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f4e1-129">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f4e1-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4e1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f4e1-130">See Also</span></span>  
 [<span data-ttu-id="6f4e1-131">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="6f4e1-131">ICLRMetaHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [<span data-ttu-id="6f4e1-132">裝載</span><span class="sxs-lookup"><span data-stu-id="6f4e1-132">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
