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
ms.openlocfilehash: 5989c45782b4f83ecfa285cb305080320abf6a3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700544"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="45417-102">IMetaDataEmit::DeleteFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="45417-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="45417-103">終結 PInvoke 封送處理指定標記所參考物件的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="45417-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45417-104">語法</span><span class="sxs-lookup"><span data-stu-id="45417-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45417-105">參數</span><span class="sxs-lookup"><span data-stu-id="45417-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="45417-106">在 `mdFieldDef` 或 `mdParamDef` token，表示要刪除封送處理中繼資料簽章的欄位或參數。</span><span class="sxs-lookup"><span data-stu-id="45417-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45417-107">需求</span><span class="sxs-lookup"><span data-stu-id="45417-107">Requirements</span></span>  

 <span data-ttu-id="45417-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45417-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45417-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="45417-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45417-110">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="45417-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45417-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45417-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45417-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45417-112">See also</span></span>

- [<span data-ttu-id="45417-113">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="45417-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="45417-114">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="45417-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
