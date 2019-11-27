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
ms.openlocfilehash: 652169c67461c1663c005dd014290c4cf2d993ba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434376"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="8b255-102">IMetaDataEmit::DeleteFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="8b255-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="8b255-103">為指定之標記所參考的物件，終結 PInvoke 封送處理中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="8b255-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b255-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b255-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b255-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b255-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="8b255-106">在`mdFieldDef` 或 `mdParamDef` token，表示要刪除封送處理中繼資料簽章的欄位或參數。</span><span class="sxs-lookup"><span data-stu-id="8b255-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b255-107">需求</span><span class="sxs-lookup"><span data-stu-id="8b255-107">Requirements</span></span>  
 <span data-ttu-id="8b255-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b255-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b255-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8b255-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b255-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8b255-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b255-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b255-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b255-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="8b255-112">See also</span></span>

- [<span data-ttu-id="8b255-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8b255-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8b255-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="8b255-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
