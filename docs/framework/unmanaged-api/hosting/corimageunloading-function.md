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
ms.openlocfilehash: a8326f95286ef05dd370797a531417f81ed5c65b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723151"
---
# <a name="_corimageunloading-function"></a><span data-ttu-id="f4950-102">_CorImageUnloading 函式</span><span class="sxs-lookup"><span data-stu-id="f4950-102">_CorImageUnloading Function</span></span>

<span data-ttu-id="f4950-103">卸載受控模組映射時，通知載入器。</span><span class="sxs-lookup"><span data-stu-id="f4950-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="f4950-104">此函數並未實作。</span><span class="sxs-lookup"><span data-stu-id="f4950-104">This function is not implemented.</span></span> <span data-ttu-id="f4950-105">如果呼叫，則會傳回 E_NOTIMPL。</span><span class="sxs-lookup"><span data-stu-id="f4950-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4950-106">語法</span><span class="sxs-lookup"><span data-stu-id="f4950-106">Syntax</span></span>  
  
```cpp  
STDAPI (VOID) _CorImageUnloading(
   [in] PVOID* ImageBase  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4950-107">參數</span><span class="sxs-lookup"><span data-stu-id="f4950-107">Parameters</span></span>  

 `ImageBase`  
 <span data-ttu-id="f4950-108">在要卸載之映射的起始位置指標。</span><span class="sxs-lookup"><span data-stu-id="f4950-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4950-109">需求</span><span class="sxs-lookup"><span data-stu-id="f4950-109">Requirements</span></span>  

 <span data-ttu-id="f4950-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4950-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4950-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f4950-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4950-112">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f4950-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4950-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4950-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4950-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4950-114">See also</span></span>

- [<span data-ttu-id="f4950-115">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f4950-115">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
