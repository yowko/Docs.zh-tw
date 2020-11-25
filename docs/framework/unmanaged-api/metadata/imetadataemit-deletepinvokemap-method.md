---
title: IMetaDataEmit::DeletePinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 6fc6cf9b7333dd4caad3c5a4b081fecb060c8f86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722085"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="5a785-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="5a785-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="5a785-103">終結指定標記所參考物件的 PInvoke 對應中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5a785-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a785-104">語法</span><span class="sxs-lookup"><span data-stu-id="5a785-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a785-105">參數</span><span class="sxs-lookup"><span data-stu-id="5a785-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="5a785-106">在 `mdFieldDef` 或 `mdMethodDef` token，表示要刪除 PInvoke 對應中繼資料的物件。</span><span class="sxs-lookup"><span data-stu-id="5a785-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a785-107">需求</span><span class="sxs-lookup"><span data-stu-id="5a785-107">Requirements</span></span>  

 <span data-ttu-id="5a785-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5a785-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a785-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5a785-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a785-110">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5a785-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a785-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a785-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a785-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a785-112">See also</span></span>

- [<span data-ttu-id="5a785-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="5a785-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5a785-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="5a785-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
