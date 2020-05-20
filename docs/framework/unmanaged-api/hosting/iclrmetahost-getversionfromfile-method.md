---
title: ICLRMetaHost::GetVersionFromFile 方法
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: 40efc256dde13d645d43f50bb574d73b5668919c
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703733"
---
# <a name="iclrmetahostgetversionfromfile-method"></a><span data-ttu-id="baa15-102">ICLRMetaHost::GetVersionFromFile 方法</span><span class="sxs-lookup"><span data-stu-id="baa15-102">ICLRMetaHost::GetVersionFromFile Method</span></span>
<span data-ttu-id="baa15-103">取得元件的原始 .NET Framework 編譯版本（儲存在中繼資料中），並指定其檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="baa15-103">Gets an assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="baa15-104">這個方法會取代[GetFileVersion](getfileversion-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="baa15-104">This method supersedes the [GetFileVersion](getfileversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa15-105">語法</span><span class="sxs-lookup"><span data-stu-id="baa15-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baa15-106">參數</span><span class="sxs-lookup"><span data-stu-id="baa15-106">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="baa15-107">在完整的元件檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="baa15-107">[in] The complete assembly file path.</span></span>  
  
 `pwzbuffer`  
 <span data-ttu-id="baa15-108">脫銷儲存在中繼資料中的 .NET Framework 編譯版本，格式為 "v*A*。*B*[。*X*] "。</span><span class="sxs-lookup"><span data-stu-id="baa15-108">[out] The .NET Framework compilation version stored in the metadata, in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="baa15-109">*A*、 *B*和*X*是對應至主要版本、次要版本和組建編號的十進位數。</span><span class="sxs-lookup"><span data-stu-id="baa15-109">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="baa15-110">此字串的長度限制為 MAX_PATH。</span><span class="sxs-lookup"><span data-stu-id="baa15-110">The length of this string is limited to MAX_PATH.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baa15-111">此輸出符合 .NET Framework 版本的目錄名稱，因為它出現在 C:\Windows\Microsoft.NET\Framework。</span><span class="sxs-lookup"><span data-stu-id="baa15-111">This output matches the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="baa15-112">範例值為 "v v1.0.3705"、"v 1.1.4322"、"v 2.0.50727" 和 "v4.0"。*X*"，其中*X*取決於安裝的組建編號。</span><span class="sxs-lookup"><span data-stu-id="baa15-112">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*X*", where *X* depends on the build number installed.</span></span> <span data-ttu-id="baa15-113">請注意，需要 "v" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="baa15-113">Note that the "v" prefix is required.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="baa15-114">[in、out]`pwzbuffer`要避免緩衝區溢位的大小。</span><span class="sxs-lookup"><span data-stu-id="baa15-114">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baa15-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="baa15-115">Return Value</span></span>  
 <span data-ttu-id="baa15-116">這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。</span><span class="sxs-lookup"><span data-stu-id="baa15-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="baa15-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baa15-117">HRESULT</span></span>|<span data-ttu-id="baa15-118">說明</span><span class="sxs-lookup"><span data-stu-id="baa15-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baa15-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="baa15-119">S_OK</span></span>|<span data-ttu-id="baa15-120">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="baa15-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="baa15-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="baa15-121">E_POINTER</span></span>|<span data-ttu-id="baa15-122">`pwzbuffer` 或 `pcchBuffer` 為 null。</span><span class="sxs-lookup"><span data-stu-id="baa15-122">`pwzbuffer` or `pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="baa15-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="baa15-123">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="baa15-124">緩衝區太小。</span><span class="sxs-lookup"><span data-stu-id="baa15-124">The buffer is too small.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="baa15-125">需求</span><span class="sxs-lookup"><span data-stu-id="baa15-125">Requirements</span></span>  
 <span data-ttu-id="baa15-126">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="baa15-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa15-127">**標頭：** MetaHost。h</span><span class="sxs-lookup"><span data-stu-id="baa15-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="baa15-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="baa15-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="baa15-129">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa15-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa15-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baa15-130">See also</span></span>

- [<span data-ttu-id="baa15-131">ICLRMetaHost 介面</span><span class="sxs-lookup"><span data-stu-id="baa15-131">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="baa15-132">裝載</span><span class="sxs-lookup"><span data-stu-id="baa15-132">Hosting</span></span>](index.md)
