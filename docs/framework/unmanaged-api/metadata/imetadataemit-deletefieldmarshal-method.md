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
ms.openlocfilehash: cf9cc16ba2702e814f27adb009a5e9b63acc97e3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500185"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="11c54-102">IMetaDataEmit::DeleteFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="11c54-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="11c54-103">終結的 PInvoke 封送處理指定的語彙基元所參考之物件的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="11c54-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c54-104">語法</span><span class="sxs-lookup"><span data-stu-id="11c54-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11c54-105">參數</span><span class="sxs-lookup"><span data-stu-id="11c54-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="11c54-106">[in]`mdFieldDef`或`mdParamDef`語彙基元，表示要刪除封送處理的中繼資料簽章的參數的欄位。</span><span class="sxs-lookup"><span data-stu-id="11c54-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11c54-107">需求</span><span class="sxs-lookup"><span data-stu-id="11c54-107">Requirements</span></span>  
 <span data-ttu-id="11c54-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="11c54-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11c54-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11c54-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11c54-110">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="11c54-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11c54-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11c54-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c54-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11c54-112">See also</span></span>
- [<span data-ttu-id="11c54-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="11c54-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11c54-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="11c54-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
