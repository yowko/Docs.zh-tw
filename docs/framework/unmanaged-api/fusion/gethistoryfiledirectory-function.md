---
title: "GetHistoryFileDirectory 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d0ec18a4f95d0d280a66b3b9d9200c560f5f187
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="4af8d-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="4af8d-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="4af8d-103">擷取應用程式的歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="4af8d-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4af8d-104">Syntax</span></span>  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4af8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4af8d-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="4af8d-106">[out]緩衝區來保存應用程式的歷程記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="4af8d-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="4af8d-107">[in、 out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="4af8d-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4af8d-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="4af8d-108">Return Value</span></span>  
 <span data-ttu-id="4af8d-109">這個方法會傳回標準的 COM 錯誤代碼，除了下列的值 WinError.h 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="4af8d-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="4af8d-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="4af8d-110">Return code</span></span>|<span data-ttu-id="4af8d-111">描述</span><span class="sxs-lookup"><span data-stu-id="4af8d-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4af8d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4af8d-112">S_OK</span></span>|<span data-ttu-id="4af8d-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="4af8d-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="4af8d-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4af8d-114">E_INVALIDARG</span></span>|<span data-ttu-id="4af8d-115">`wzDir`或`pdwSize`是 null 或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="4af8d-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4af8d-116">備註</span><span class="sxs-lookup"><span data-stu-id="4af8d-116">Remarks</span></span>  
 <span data-ttu-id="4af8d-117">成功完成，`pdwSize`引數的設定路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="4af8d-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4af8d-118">需求</span><span class="sxs-lookup"><span data-stu-id="4af8d-118">Requirements</span></span>  
 <span data-ttu-id="4af8d-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4af8d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4af8d-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4af8d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4af8d-121">**程式庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="4af8d-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="4af8d-122">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="4af8d-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="4af8d-123">**.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4af8d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4af8d-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="4af8d-124">See Also</span></span>  
 [<span data-ttu-id="4af8d-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="4af8d-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="4af8d-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="4af8d-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 [<span data-ttu-id="4af8d-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="4af8d-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
