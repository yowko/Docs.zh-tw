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
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697614"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="94c66-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="94c66-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="94c66-103">擷取應用程式記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="94c66-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c66-104">語法</span><span class="sxs-lookup"><span data-stu-id="94c66-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94c66-105">參數</span><span class="sxs-lookup"><span data-stu-id="94c66-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="94c66-106">[out]緩衝區的緩衝區來保存應用程式記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="94c66-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="94c66-107">[in、 out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="94c66-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94c66-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="94c66-108">Return Value</span></span>  
 <span data-ttu-id="94c66-109">這個方法會傳回標準 COM 錯誤碼，定義在 WinError.h 檔案中，除了下列的值。</span><span class="sxs-lookup"><span data-stu-id="94c66-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="94c66-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="94c66-110">Return code</span></span>|<span data-ttu-id="94c66-111">描述</span><span class="sxs-lookup"><span data-stu-id="94c66-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="94c66-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="94c66-112">S_OK</span></span>|<span data-ttu-id="94c66-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="94c66-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="94c66-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="94c66-114">E_INVALIDARG</span></span>|<span data-ttu-id="94c66-115">`wzDir` 或`pdwSize`是 null 或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="94c66-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94c66-116">備註</span><span class="sxs-lookup"><span data-stu-id="94c66-116">Remarks</span></span>  
 <span data-ttu-id="94c66-117">成功完成時，`pdwSize`引數設定為路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="94c66-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94c66-118">需求</span><span class="sxs-lookup"><span data-stu-id="94c66-118">Requirements</span></span>  
 <span data-ttu-id="94c66-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94c66-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94c66-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="94c66-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="94c66-121">**LIBRARY:** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="94c66-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="94c66-122">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 的正確版本。</span><span class="sxs-lookup"><span data-stu-id="94c66-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="94c66-123">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94c66-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c66-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94c66-124">See also</span></span>

- [<span data-ttu-id="94c66-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="94c66-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="94c66-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="94c66-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="94c66-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="94c66-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
