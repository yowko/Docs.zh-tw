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
ms.openlocfilehash: bba40acf7bfd20897ece4de285fe7a9175be83e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431759"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="3a760-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="3a760-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="3a760-103">擷取應用程式的歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="3a760-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a760-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a760-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a760-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a760-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="3a760-106">[out]緩衝區來保存應用程式的歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="3a760-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="3a760-107">[in、 out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="3a760-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a760-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3a760-108">Return Value</span></span>  
 <span data-ttu-id="3a760-109">這個方法會傳回標準的 COM 錯誤代碼，除了下列的值 WinError.h 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="3a760-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="3a760-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="3a760-110">Return code</span></span>|<span data-ttu-id="3a760-111">描述</span><span class="sxs-lookup"><span data-stu-id="3a760-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3a760-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a760-112">S_OK</span></span>|<span data-ttu-id="3a760-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="3a760-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="3a760-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3a760-114">E_INVALIDARG</span></span>|<span data-ttu-id="3a760-115">`wzDir` 或`pdwSize`是 null 或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="3a760-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a760-116">備註</span><span class="sxs-lookup"><span data-stu-id="3a760-116">Remarks</span></span>  
 <span data-ttu-id="3a760-117">成功完成，`pdwSize`引數的設定路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="3a760-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a760-118">需求</span><span class="sxs-lookup"><span data-stu-id="3a760-118">Requirements</span></span>  
 <span data-ttu-id="3a760-119">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a760-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a760-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3a760-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3a760-121">**程式庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="3a760-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="3a760-122">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="3a760-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="3a760-123">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a760-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a760-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a760-124">See Also</span></span>  
 [<span data-ttu-id="3a760-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="3a760-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="3a760-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="3a760-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="3a760-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3a760-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
