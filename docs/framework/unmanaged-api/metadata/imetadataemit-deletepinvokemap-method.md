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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3b7c116410ce3309d970929580f4ec7f65bd657
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558276"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="7dfeb-102">IMetaDataEmit::DeletePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="7dfeb-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="7dfeb-103">終結指定的語彙基元所參考物件的 PInvoke 對應中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7dfeb-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dfeb-104">語法</span><span class="sxs-lookup"><span data-stu-id="7dfeb-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dfeb-105">參數</span><span class="sxs-lookup"><span data-stu-id="7dfeb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7dfeb-106">[in]`mdFieldDef`或`mdMethodDef`語彙基元，表示要刪除的 PInvoke 對應中繼資料物件。</span><span class="sxs-lookup"><span data-stu-id="7dfeb-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dfeb-107">需求</span><span class="sxs-lookup"><span data-stu-id="7dfeb-107">Requirements</span></span>  
 <span data-ttu-id="7dfeb-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfeb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dfeb-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7dfeb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7dfeb-110">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7dfeb-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7dfeb-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dfeb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfeb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfeb-112">See also</span></span>
- [<span data-ttu-id="7dfeb-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="7dfeb-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7dfeb-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="7dfeb-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
