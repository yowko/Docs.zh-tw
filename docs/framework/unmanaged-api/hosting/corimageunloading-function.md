---
title: _CorImageUnloading 函式
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 72c851858ab2f294601d2e7f97b43e21ca815857
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474813"
---
# <a name="corimageunloading-function"></a><span data-ttu-id="542e1-102">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="542e1-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="542e1-103">卸載 managed 的模組映像時，請通知載入器。</span><span class="sxs-lookup"><span data-stu-id="542e1-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="542e1-104">未實作此函式。</span><span class="sxs-lookup"><span data-stu-id="542e1-104">This function is not implemented.</span></span> <span data-ttu-id="542e1-105">如果呼叫，它會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="542e1-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="542e1-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="542e1-107">參數</span><span class="sxs-lookup"><span data-stu-id="542e1-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="542e1-108">[in]要卸載之影像的起始位置指標。</span><span class="sxs-lookup"><span data-stu-id="542e1-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="542e1-109">需求</span><span class="sxs-lookup"><span data-stu-id="542e1-109">Requirements</span></span>  
 <span data-ttu-id="542e1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="542e1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="542e1-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="542e1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="542e1-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="542e1-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="542e1-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="542e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542e1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="542e1-114">See also</span></span>
- [<span data-ttu-id="542e1-115">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="542e1-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
