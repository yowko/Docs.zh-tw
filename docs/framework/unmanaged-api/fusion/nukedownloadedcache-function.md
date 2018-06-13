---
title: NukeDownloadedCache 函式
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429823"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="cd6db-102">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="cd6db-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="cd6db-103">刪除 common language runtime (CLR) 下載快取。</span><span class="sxs-lookup"><span data-stu-id="cd6db-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd6db-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd6db-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="cd6db-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd6db-105">Return Value</span></span>  
 <span data-ttu-id="cd6db-106">這個方法會傳回標準的 COM 錯誤代碼，WinError.h 中定義。</span><span class="sxs-lookup"><span data-stu-id="cd6db-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd6db-107">備註</span><span class="sxs-lookup"><span data-stu-id="cd6db-107">Remarks</span></span>  
 <span data-ttu-id="cd6db-108">CLR 下載快取是從 URL 下載的強式名稱組件可能重複使用的儲存位置的區域。</span><span class="sxs-lookup"><span data-stu-id="cd6db-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd6db-109">需求</span><span class="sxs-lookup"><span data-stu-id="cd6db-109">Requirements</span></span>  
 <span data-ttu-id="cd6db-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cd6db-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6db-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="cd6db-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="cd6db-112">**程式庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="cd6db-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="cd6db-113">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="cd6db-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="cd6db-114">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6db-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6db-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd6db-115">See Also</span></span>  
 [<span data-ttu-id="cd6db-116">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="cd6db-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="cd6db-117">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="cd6db-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="cd6db-118">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="cd6db-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
