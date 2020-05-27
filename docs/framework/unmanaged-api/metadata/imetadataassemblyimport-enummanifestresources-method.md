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
ms.openlocfilehash: 560a6adf85fab7f421b86cba52224d5b1bfe1089
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006255"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="6cb23-102">IMetaDataAssemblyImport::EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="6cb23-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="6cb23-103">取得目前組件資訊清單中所參考資源的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="6cb23-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cb23-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cb23-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,
    [out] mdManifestResource   rManifestResources[],
    [in]  ULONG                cMax,
    [out] ULONG                *pcTokens  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="6cb23-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cb23-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6cb23-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="6cb23-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6cb23-107">第一次呼叫方法時，這必須是 null 值 `EnumManifestResources` 。</span><span class="sxs-lookup"><span data-stu-id="6cb23-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="6cb23-108">脫銷用來儲存 `mdManifestResource` 元資料標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="6cb23-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6cb23-109">在`mdManifestResource`可以放入的標記數目上限 `rManifestResources` 。</span><span class="sxs-lookup"><span data-stu-id="6cb23-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6cb23-110">脫銷`mdManifestResource`實際放入的權杖數目 `rManifestResources` 。</span><span class="sxs-lookup"><span data-stu-id="6cb23-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cb23-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cb23-111">Return Value</span></span>  
  
|<span data-ttu-id="6cb23-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cb23-112">HRESULT</span></span>|<span data-ttu-id="6cb23-113">描述</span><span class="sxs-lookup"><span data-stu-id="6cb23-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6cb23-114">`EnumManifestResources`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6cb23-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6cb23-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="6cb23-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6cb23-116">在此情況下， `pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="6cb23-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cb23-117">需求</span><span class="sxs-lookup"><span data-stu-id="6cb23-117">Requirements</span></span>  
 <span data-ttu-id="6cb23-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cb23-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb23-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6cb23-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cb23-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6cb23-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cb23-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cb23-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cb23-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cb23-122">See also</span></span>

- [<span data-ttu-id="6cb23-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="6cb23-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
