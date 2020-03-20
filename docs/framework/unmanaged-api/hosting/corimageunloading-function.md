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
ms.openlocfilehash: 4932e1fd6294f4a01264e982835dd0707324082a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178225"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="38c06-102">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="38c06-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="38c06-103">卸載託管模組映射時通知載入程式。</span><span class="sxs-lookup"><span data-stu-id="38c06-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="38c06-104">此函數並未實作。</span><span class="sxs-lookup"><span data-stu-id="38c06-104">This function is not implemented.</span></span> <span data-ttu-id="38c06-105">如果調用，它將返回E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="38c06-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c06-106">語法</span><span class="sxs-lookup"><span data-stu-id="38c06-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38c06-107">參數</span><span class="sxs-lookup"><span data-stu-id="38c06-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="38c06-108">[在]指向要卸載的圖像的起始位置的指標。</span><span class="sxs-lookup"><span data-stu-id="38c06-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38c06-109">需求</span><span class="sxs-lookup"><span data-stu-id="38c06-109">Requirements</span></span>  
 <span data-ttu-id="38c06-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38c06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38c06-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="38c06-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38c06-112">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="38c06-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38c06-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38c06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c06-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38c06-114">See also</span></span>

- [<span data-ttu-id="38c06-115">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="38c06-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
