---
title: "ClearDownloadCache 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClearDownloadCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: ClearDownloadCache
helpviewer_keywords: ClearDownloadCache function [.NET Framework fusion]
ms.assetid: df7595d1-430f-44b4-8160-4c2ba9df70b1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffd3eb58a471e5685b34aaae634f6d200375b0eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cleardownloadcache-function"></a><span data-ttu-id="7f5b1-102">ClearDownloadCache 函式</span><span class="sxs-lookup"><span data-stu-id="7f5b1-102">ClearDownloadCache Function</span></span>
<span data-ttu-id="7f5b1-103">清除已下載組件的全域組件快取。</span><span class="sxs-lookup"><span data-stu-id="7f5b1-103">Clears the global assembly cache of downloaded assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f5b1-104">Syntax</span></span>  
  
```  
HRESULT ClearDownloadCache ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7f5b1-105">需求</span><span class="sxs-lookup"><span data-stu-id="7f5b1-105">Requirements</span></span>  
 <span data-ttu-id="7f5b1-106">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f5b1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5b1-107">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7f5b1-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7f5b1-108">**程式庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="7f5b1-108">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="7f5b1-109">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="7f5b1-109">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="7f5b1-110">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5b1-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5b1-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="7f5b1-111">See Also</span></span>  
 [<span data-ttu-id="7f5b1-112">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="7f5b1-112">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="7f5b1-113">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="7f5b1-113">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
