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
ms.openlocfilehash: 17757df566ba8d141e7adec00dcc1f75959d0e00
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005621"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="afa4c-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="afa4c-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="afa4c-103">使用指定的中繼資料簽章，建立自訂屬性的定義，以附加至指定的物件，並取得該自訂屬性定義的 token。</span><span class="sxs-lookup"><span data-stu-id="afa4c-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afa4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="afa4c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afa4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="afa4c-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="afa4c-106">在擁有者專案的 token。</span><span class="sxs-lookup"><span data-stu-id="afa4c-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="afa4c-107">在識別自訂屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="afa4c-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="afa4c-108">在自訂屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="afa4c-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="afa4c-109">在中的位元組計數 `pCustomAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="afa4c-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="afa4c-110">脫銷`mdCustomAttribute`指派的 token。</span><span class="sxs-lookup"><span data-stu-id="afa4c-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afa4c-111">需求</span><span class="sxs-lookup"><span data-stu-id="afa4c-111">Requirements</span></span>  
 <span data-ttu-id="afa4c-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="afa4c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afa4c-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="afa4c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afa4c-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="afa4c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afa4c-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afa4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa4c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afa4c-116">See also</span></span>

- [<span data-ttu-id="afa4c-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="afa4c-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="afa4c-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="afa4c-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
