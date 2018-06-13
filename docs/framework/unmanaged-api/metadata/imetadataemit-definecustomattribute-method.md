---
title: IMetaDataEmit::DefineCustomAttribute 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a11e9919dc1338c4b67c3c4b0f082e330c29d9eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445078"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="2352e-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="2352e-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="2352e-103">建立自訂屬性的定義，使用指定的中繼資料簽章附加到指定的物件，並取得該自訂屬性定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2352e-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2352e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2352e-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2352e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2352e-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="2352e-106">[in]擁有者項目之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2352e-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="2352e-107">[in]自訂屬性可識別的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2352e-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="2352e-108">[in]指向的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="2352e-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="2352e-109">[in]中的位元組計數`pCustomAttribute`。</span><span class="sxs-lookup"><span data-stu-id="2352e-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="2352e-110">[out]`mdCustomAttribute`指派的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2352e-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2352e-111">需求</span><span class="sxs-lookup"><span data-stu-id="2352e-111">Requirements</span></span>  
 <span data-ttu-id="2352e-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2352e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2352e-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2352e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2352e-114">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2352e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2352e-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2352e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2352e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2352e-116">See Also</span></span>  
 [<span data-ttu-id="2352e-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2352e-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="2352e-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="2352e-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
