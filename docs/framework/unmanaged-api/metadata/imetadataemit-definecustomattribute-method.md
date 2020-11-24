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
ms.openlocfilehash: 096a460f9d6581ebdd00f8487af68f652524d52f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681661"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="189c8-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="189c8-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>

<span data-ttu-id="189c8-103">使用指定的中繼資料簽章來建立自訂屬性的定義，以附加至指定的物件，並取得該自訂屬性定義的標記。</span><span class="sxs-lookup"><span data-stu-id="189c8-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189c8-104">語法</span><span class="sxs-lookup"><span data-stu-id="189c8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="189c8-105">參數</span><span class="sxs-lookup"><span data-stu-id="189c8-105">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="189c8-106">在擁有者專案的標記。</span><span class="sxs-lookup"><span data-stu-id="189c8-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="189c8-107">在識別自訂屬性的標記。</span><span class="sxs-lookup"><span data-stu-id="189c8-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="189c8-108">在自訂屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="189c8-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="189c8-109">在中的位元組計數 `pCustomAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="189c8-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="189c8-110">擴展 `mdCustomAttribute` 指派的權杖。</span><span class="sxs-lookup"><span data-stu-id="189c8-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="189c8-111">需求</span><span class="sxs-lookup"><span data-stu-id="189c8-111">Requirements</span></span>  

 <span data-ttu-id="189c8-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="189c8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="189c8-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="189c8-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="189c8-114">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="189c8-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="189c8-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="189c8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189c8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="189c8-116">See also</span></span>

- [<span data-ttu-id="189c8-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="189c8-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="189c8-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="189c8-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
