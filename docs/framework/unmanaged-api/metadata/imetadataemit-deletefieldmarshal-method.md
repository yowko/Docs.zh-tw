---
title: IMetaDataEmit::DeleteFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36f9ac10348cb8235c95070ddbc9cb5f47a84bd6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777448"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="4ebf5-102">IMetaDataEmit::DeleteFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="4ebf5-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="4ebf5-103">終結的 PInvoke 封送處理指定的語彙基元所參考之物件的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="4ebf5-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ebf5-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ebf5-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ebf5-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ebf5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="4ebf5-106">[in]`mdFieldDef`或`mdParamDef`語彙基元，表示要刪除封送處理的中繼資料簽章的參數的欄位。</span><span class="sxs-lookup"><span data-stu-id="4ebf5-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ebf5-107">需求</span><span class="sxs-lookup"><span data-stu-id="4ebf5-107">Requirements</span></span>  
 <span data-ttu-id="4ebf5-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ebf5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ebf5-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4ebf5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ebf5-110">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4ebf5-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ebf5-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ebf5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebf5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ebf5-112">See also</span></span>

- [<span data-ttu-id="4ebf5-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4ebf5-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4ebf5-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4ebf5-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
