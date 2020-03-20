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
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175885"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="51f21-102">IMetaDataEmit::DefineCustomAttribute 方法</span><span class="sxs-lookup"><span data-stu-id="51f21-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="51f21-103">為具有指定中繼資料簽名的自訂屬性創建要附加到指定物件的定義，並獲取該自訂屬性定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="51f21-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51f21-104">語法</span><span class="sxs-lookup"><span data-stu-id="51f21-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51f21-105">參數</span><span class="sxs-lookup"><span data-stu-id="51f21-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="51f21-106">[在]擁有者項的權杖。</span><span class="sxs-lookup"><span data-stu-id="51f21-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="51f21-107">[在]標識自訂屬性的權杖。</span><span class="sxs-lookup"><span data-stu-id="51f21-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="51f21-108">[在]指向自訂屬性的指標。</span><span class="sxs-lookup"><span data-stu-id="51f21-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="51f21-109">[在]中的`pCustomAttribute`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="51f21-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="51f21-110">[出]分配的`mdCustomAttribute`權杖。</span><span class="sxs-lookup"><span data-stu-id="51f21-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51f21-111">需求</span><span class="sxs-lookup"><span data-stu-id="51f21-111">Requirements</span></span>  
 <span data-ttu-id="51f21-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51f21-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51f21-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="51f21-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51f21-114">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51f21-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51f21-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51f21-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f21-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51f21-116">See also</span></span>

- [<span data-ttu-id="51f21-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="51f21-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="51f21-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="51f21-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
