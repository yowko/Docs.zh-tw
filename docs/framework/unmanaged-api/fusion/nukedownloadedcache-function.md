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
ms.openlocfilehash: 8f97614412eb2d49b202e86bdabc727159deb5d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131690"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="ae942-102">NukeDownloadedCache 函式</span><span class="sxs-lookup"><span data-stu-id="ae942-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="ae942-103">刪除 common language runtime （CLR）下載快取。</span><span class="sxs-lookup"><span data-stu-id="ae942-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae942-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae942-104">Syntax</span></span>  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ae942-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="ae942-105">Return Value</span></span>  
 <span data-ttu-id="ae942-106">這個方法會傳回標準 COM 錯誤碼（如 Winerror.h 中所定義）。</span><span class="sxs-lookup"><span data-stu-id="ae942-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae942-107">備註</span><span class="sxs-lookup"><span data-stu-id="ae942-107">Remarks</span></span>  
 <span data-ttu-id="ae942-108">CLR 下載快取是用來儲存從 URL 下載之強式名稱元件的區域，以供重複使用。</span><span class="sxs-lookup"><span data-stu-id="ae942-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae942-109">需求</span><span class="sxs-lookup"><span data-stu-id="ae942-109">Requirements</span></span>  
 <span data-ttu-id="ae942-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae942-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae942-111">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="ae942-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ae942-112">連結**庫：** 融合 .dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="ae942-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="ae942-113">請使用 [Mscorwks.dll]，而不是 []，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="ae942-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="ae942-114">**.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae942-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae942-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae942-115">See also</span></span>

- [<span data-ttu-id="ae942-116">CreateHistoryReader 函式</span><span class="sxs-lookup"><span data-stu-id="ae942-116">CreateHistoryReader Function</span></span>](createhistoryreader-function.md)
- [<span data-ttu-id="ae942-117">GetHistoryFileDirectory 函式</span><span class="sxs-lookup"><span data-stu-id="ae942-117">GetHistoryFileDirectory Function</span></span>](gethistoryfiledirectory-function.md)
- [<span data-ttu-id="ae942-118">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ae942-118">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
