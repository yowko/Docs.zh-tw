---
title: ClearDownloadCache 函式
ms.date: 03/30/2017
api_name:
- ClearDownloadCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- ClearDownloadCache
helpviewer_keywords:
- ClearDownloadCache function [.NET Framework fusion]
ms.assetid: df7595d1-430f-44b4-8160-4c2ba9df70b1
topic_type:
- apiref
ms.openlocfilehash: a280b071b3c9f390e59d60009b5b9ed1c136989b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731094"
---
# <a name="cleardownloadcache-function"></a><span data-ttu-id="9c6a5-102">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="9c6a5-102">ClearDownloadCache Function</span></span>

<span data-ttu-id="9c6a5-103">清除已下載元件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="9c6a5-103">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c6a5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9c6a5-104">Syntax</span></span>  
  
```cpp  
HRESULT ClearDownloadCache ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9c6a5-105">需求</span><span class="sxs-lookup"><span data-stu-id="9c6a5-105">Requirements</span></span>  

 <span data-ttu-id="9c6a5-106">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c6a5-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c6a5-107">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="9c6a5-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9c6a5-108">連結 **庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="9c6a5-108">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="9c6a5-109">使用 Fusion.dll 而不是 Mscorwks.dll，以確保您以正確的 .NET Framework 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="9c6a5-109">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="9c6a5-110">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c6a5-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c6a5-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c6a5-111">See also</span></span>

- [<span data-ttu-id="9c6a5-112">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="9c6a5-112">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="9c6a5-113">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="9c6a5-113">Global Assembly Cache</span></span>](../../app-domains/gac.md)
