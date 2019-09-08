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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: adbbf94dc36c6d82360ed532b283cd666a1a52ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796857"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="d59b3-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="d59b3-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="d59b3-103">抓取應用程式歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="d59b3-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d59b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d59b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d59b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d59b3-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="d59b3-106">脫銷保存應用程式歷程記錄目錄路徑的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="d59b3-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="d59b3-107">[in、out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="d59b3-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d59b3-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="d59b3-108">Return Value</span></span>  
 <span data-ttu-id="d59b3-109">除了下列值之外，這個方法會傳回 Winerror.h 檔案中定義的標準 COM 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d59b3-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="d59b3-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="d59b3-110">Return code</span></span>|<span data-ttu-id="d59b3-111">描述</span><span class="sxs-lookup"><span data-stu-id="d59b3-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d59b3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d59b3-112">S_OK</span></span>|<span data-ttu-id="d59b3-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="d59b3-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d59b3-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d59b3-114">E_INVALIDARG</span></span>|<span data-ttu-id="d59b3-115">`wzDir`或`pdwSize`為 null，或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="d59b3-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d59b3-116">備註</span><span class="sxs-lookup"><span data-stu-id="d59b3-116">Remarks</span></span>  
 <span data-ttu-id="d59b3-117">成功完成時， `pdwSize`引數會設定為路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="d59b3-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d59b3-118">需求</span><span class="sxs-lookup"><span data-stu-id="d59b3-118">Requirements</span></span>  
 <span data-ttu-id="d59b3-119">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d59b3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d59b3-120">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="d59b3-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d59b3-121">**LIBRARY:** 融合 .dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="d59b3-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="d59b3-122">請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="d59b3-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d59b3-123">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d59b3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d59b3-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d59b3-124">See also</span></span>

- [<span data-ttu-id="d59b3-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="d59b3-125">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="d59b3-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="d59b3-126">NukeDownloadedCache Function</span></span>](nukedownloadedcache-function.md)
- [<span data-ttu-id="d59b3-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d59b3-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
