---
title: IMetaDataAssemblyImport::EnumManifestResources 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumManifestResources
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumManifestResources
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumManifestResources method [.NET Framework metadata]
- EnumManifestResources method [.NET Framework metadata]
ms.assetid: 9543b111-5705-40c9-935c-a3ffc7a581aa
topic_type:
- apiref
ms.openlocfilehash: 22141cf46a965c0624c076bd1d86d2624e5a09f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176015"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="80e1f-102">IMetaDataAssemblyImport::EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="80e1f-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="80e1f-103">獲取當前組件資訊清單中引用的資源的指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="80e1f-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="80e1f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="80e1f-105">參數</span><span class="sxs-lookup"><span data-stu-id="80e1f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="80e1f-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="80e1f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="80e1f-107">當首次調用該方法時，`EnumManifestResources`這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="80e1f-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="80e1f-108">[出]用於存儲中繼資料權杖的`mdManifestResource`陣列。</span><span class="sxs-lookup"><span data-stu-id="80e1f-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="80e1f-109">[在]可放置在 中`mdManifestResource`的最大權杖數`rManifestResources`。</span><span class="sxs-lookup"><span data-stu-id="80e1f-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="80e1f-110">[出]實際放置在`mdManifestResource`中的`rManifestResources`權杖數。</span><span class="sxs-lookup"><span data-stu-id="80e1f-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80e1f-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="80e1f-111">Return Value</span></span>  
  
|<span data-ttu-id="80e1f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="80e1f-112">HRESULT</span></span>|<span data-ttu-id="80e1f-113">描述</span><span class="sxs-lookup"><span data-stu-id="80e1f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="80e1f-114">`EnumManifestResources`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="80e1f-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="80e1f-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="80e1f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="80e1f-116">在這種情況下，`pcTokens`設置為零。</span><span class="sxs-lookup"><span data-stu-id="80e1f-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80e1f-117">需求</span><span class="sxs-lookup"><span data-stu-id="80e1f-117">Requirements</span></span>  
 <span data-ttu-id="80e1f-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80e1f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e1f-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="80e1f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80e1f-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="80e1f-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80e1f-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e1f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e1f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e1f-122">See also</span></span>

- [<span data-ttu-id="80e1f-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="80e1f-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
