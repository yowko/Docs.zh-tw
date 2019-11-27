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
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432647"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="b37a6-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="b37a6-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="b37a6-103">使用指定的中繼資料簽章，建立自訂屬性的定義，以附加至指定的物件，並取得該自訂屬性定義的 token。</span><span class="sxs-lookup"><span data-stu-id="b37a6-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b37a6-104">語法</span><span class="sxs-lookup"><span data-stu-id="b37a6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b37a6-105">參數</span><span class="sxs-lookup"><span data-stu-id="b37a6-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="b37a6-106">在擁有者專案的 token。</span><span class="sxs-lookup"><span data-stu-id="b37a6-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="b37a6-107">在識別自訂屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="b37a6-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="b37a6-108">在自訂屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="b37a6-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="b37a6-109">在`pCustomAttribute`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="b37a6-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="b37a6-110">脫銷指派的 `mdCustomAttribute` token。</span><span class="sxs-lookup"><span data-stu-id="b37a6-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b37a6-111">需求</span><span class="sxs-lookup"><span data-stu-id="b37a6-111">Requirements</span></span>  
 <span data-ttu-id="b37a6-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b37a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b37a6-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b37a6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b37a6-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b37a6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b37a6-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b37a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b37a6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b37a6-116">See also</span></span>

- [<span data-ttu-id="b37a6-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b37a6-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b37a6-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b37a6-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
