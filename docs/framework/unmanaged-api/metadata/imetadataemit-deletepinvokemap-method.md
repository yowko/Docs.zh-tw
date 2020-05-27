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
ms.openlocfilehash: 79af7b5679598ffa82471dcb69adabc2394b13fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009297"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="b95ce-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="b95ce-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="b95ce-103">為指定之標記所參考的物件，終結 PInvoke 對應中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b95ce-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b95ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="b95ce-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b95ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="b95ce-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b95ce-106">在`mdFieldDef`或 `mdMethodDef` token，表示要刪除 PInvoke 對應中繼資料的物件。</span><span class="sxs-lookup"><span data-stu-id="b95ce-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b95ce-107">需求</span><span class="sxs-lookup"><span data-stu-id="b95ce-107">Requirements</span></span>  
 <span data-ttu-id="b95ce-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b95ce-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b95ce-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b95ce-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b95ce-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b95ce-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b95ce-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b95ce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b95ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b95ce-112">See also</span></span>

- [<span data-ttu-id="b95ce-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b95ce-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b95ce-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b95ce-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
