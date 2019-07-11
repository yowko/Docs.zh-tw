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
ms.openlocfilehash: 10eead2772a2bbd8abaf7b9c090a091687725972
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778649"
---
# <a name="gethistoryfiledirectory-function"></a><span data-ttu-id="daa2e-102">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="daa2e-102">GetHistoryFileDirectory Function</span></span>
<span data-ttu-id="daa2e-103">擷取應用程式記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="daa2e-103">Retrieves the path of the application history directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daa2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="daa2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daa2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="daa2e-105">Parameters</span></span>  
 `wzDir`  
 <span data-ttu-id="daa2e-106">[out]緩衝區的緩衝區來保存應用程式記錄目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="daa2e-106">[out] A buffer to hold the path to the application history directory.</span></span>  
  
 `pdwSize`  
 <span data-ttu-id="daa2e-107">[in、 out]緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="daa2e-107">[in, out] The length of the buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daa2e-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="daa2e-108">Return Value</span></span>  
 <span data-ttu-id="daa2e-109">這個方法會傳回標準 COM 錯誤碼，定義在 WinError.h 檔案中，除了下列的值。</span><span class="sxs-lookup"><span data-stu-id="daa2e-109">This method returns standard COM error codes, as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="daa2e-110">傳回碼</span><span class="sxs-lookup"><span data-stu-id="daa2e-110">Return code</span></span>|<span data-ttu-id="daa2e-111">描述</span><span class="sxs-lookup"><span data-stu-id="daa2e-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="daa2e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="daa2e-112">S_OK</span></span>|<span data-ttu-id="daa2e-113">已成功完成命令。</span><span class="sxs-lookup"><span data-stu-id="daa2e-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="daa2e-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="daa2e-114">E_INVALIDARG</span></span>|<span data-ttu-id="daa2e-115">`wzDir` 或`pdwSize`是 null 或版本字串不正確。</span><span class="sxs-lookup"><span data-stu-id="daa2e-115">`wzDir` or `pdwSize` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daa2e-116">備註</span><span class="sxs-lookup"><span data-stu-id="daa2e-116">Remarks</span></span>  
 <span data-ttu-id="daa2e-117">成功完成時，`pdwSize`引數設定為路徑字串的長度。</span><span class="sxs-lookup"><span data-stu-id="daa2e-117">On successful completion, the `pdwSize` argument is set to the length of the path string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa2e-118">需求</span><span class="sxs-lookup"><span data-stu-id="daa2e-118">Requirements</span></span>  
 <span data-ttu-id="daa2e-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="daa2e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa2e-120">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="daa2e-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="daa2e-121">**LIBRARY:** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="daa2e-121">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="daa2e-122">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 的正確版本。</span><span class="sxs-lookup"><span data-stu-id="daa2e-122">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="daa2e-123">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa2e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa2e-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="daa2e-124">See also</span></span>

- [<span data-ttu-id="daa2e-125">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="daa2e-125">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="daa2e-126">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="daa2e-126">NukeDownloadedCache Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [<span data-ttu-id="daa2e-127">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="daa2e-127">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
