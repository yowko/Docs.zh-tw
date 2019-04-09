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
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075661"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="db90a-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="db90a-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="db90a-103">建立自訂屬性的定義，具有指定之中繼資料簽章，附加至指定的物件，並取得該自訂屬性定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="db90a-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db90a-104">語法</span><span class="sxs-lookup"><span data-stu-id="db90a-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db90a-105">參數</span><span class="sxs-lookup"><span data-stu-id="db90a-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="db90a-106">[in]擁有者項目之語彙基元。</span><span class="sxs-lookup"><span data-stu-id="db90a-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="db90a-107">[in]語彙基元，可識別自訂的屬性。</span><span class="sxs-lookup"><span data-stu-id="db90a-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="db90a-108">[in]自訂屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="db90a-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="db90a-109">[in]中的位元組計數`pCustomAttribute`。</span><span class="sxs-lookup"><span data-stu-id="db90a-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="db90a-110">[out]`mdCustomAttribute`指派權杖。</span><span class="sxs-lookup"><span data-stu-id="db90a-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db90a-111">需求</span><span class="sxs-lookup"><span data-stu-id="db90a-111">Requirements</span></span>  
 <span data-ttu-id="db90a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db90a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db90a-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db90a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db90a-114">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="db90a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="db90a-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="db90a-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="db90a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db90a-116">See also</span></span>

- [<span data-ttu-id="db90a-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="db90a-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="db90a-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="db90a-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
