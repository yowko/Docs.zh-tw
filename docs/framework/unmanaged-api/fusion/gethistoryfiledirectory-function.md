---
title: GetHistoryFileDirectory 函式
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724434"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="37c5d-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="37c5d-102">GetHistoryFileDirectory Function</span></span>

<span data-ttu-id="37c5d-103">抓取應用程式歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="37c5d-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37c5d-104">語法</span><span class="sxs-lookup"><span data-stu-id="37c5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37c5d-105">參數</span><span class="sxs-lookup"><span data-stu-id="37c5d-105">Parameters</span></span>  

 `wzDir`  
 <span data-ttu-id="37c5d-106">擴展保存應用程式歷程記錄目錄路徑的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="37c5d-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="37c5d-107">[in，out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="37c5d-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37c5d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="37c5d-108">Return Value</span></span>  

 <span data-ttu-id="37c5d-109">除了下列值以外，這個方法會傳回 Winerror.h .h 檔案中所定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="37c5d-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="37c5d-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="37c5d-110">Return code</span></span>|<span data-ttu-id="37c5d-111">描述</span><span class="sxs-lookup"><span data-stu-id="37c5d-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="37c5d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="37c5d-112">S_OK</span></span>|<span data-ttu-id="37c5d-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="37c5d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="37c5d-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="37c5d-114">E_INVALIDARG</span></span>|<span data-ttu-id="37c5d-115">`wzDir` 或 `pdwSize` 為 null，或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="37c5d-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c5d-116">備註</span><span class="sxs-lookup"><span data-stu-id="37c5d-116">Remarks</span></span>  

 <span data-ttu-id="37c5d-117">成功完成時， `pdwSize` 引數會設定為路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="37c5d-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c5d-118">需求</span><span class="sxs-lookup"><span data-stu-id="37c5d-118">Requirements</span></span>  

 <span data-ttu-id="37c5d-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37c5d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c5d-120">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="37c5d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="37c5d-121">連結 **庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="37c5d-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="37c5d-122">使用 Fusion.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="37c5d-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="37c5d-123">**.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c5d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37c5d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37c5d-124">See also</span></span>

- [<span data-ttu-id="37c5d-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="37c5d-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="37c5d-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="37c5d-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="37c5d-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="37c5d-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
