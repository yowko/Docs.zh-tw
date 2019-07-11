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
ms.openlocfilehash: 76ada8400573dd61c25e0dce3f49ce66b5fb30c1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773810"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="bbdcc-102">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="bbdcc-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="bbdcc-103">刪除 common language runtime (CLR) 下載快取。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbdcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="bbdcc-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bbdcc-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="bbdcc-105">Return Value</span></span>  
 <span data-ttu-id="bbdcc-106">這個方法會傳回標準 COM 錯誤碼，WinError.h 中定義。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbdcc-107">備註</span><span class="sxs-lookup"><span data-stu-id="bbdcc-107">Remarks</span></span>  
 <span data-ttu-id="bbdcc-108">CLR 下載快取是從 URL 下載的強式名稱組件可能重複使用的儲存位置的區域。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdcc-109">需求</span><span class="sxs-lookup"><span data-stu-id="bbdcc-109">Requirements</span></span>  
 <span data-ttu-id="bbdcc-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdcc-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bbdcc-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bbdcc-112">**LIBRARY:** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="bbdcc-113">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 的正確版本。</span><span class="sxs-lookup"><span data-stu-id="bbdcc-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="bbdcc-114">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbdcc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdcc-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbdcc-115">See also</span></span>

- [<span data-ttu-id="bbdcc-116">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="bbdcc-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [<span data-ttu-id="bbdcc-117">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="bbdcc-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)
- [<span data-ttu-id="bbdcc-118">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="bbdcc-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
