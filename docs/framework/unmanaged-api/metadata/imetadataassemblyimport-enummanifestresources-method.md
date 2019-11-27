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
ms.openlocfilehash: 2748460826deb422a3851713db11343209fe449a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449550"
---
# <a name="imetadataassemblyimportenummanifestresources-method"></a><span data-ttu-id="353c3-102">IMetaDataAssemblyImport::EnumManifestResources 方法</span><span class="sxs-lookup"><span data-stu-id="353c3-102">IMetaDataAssemblyImport::EnumManifestResources Method</span></span>
<span data-ttu-id="353c3-103">取得目前組件資訊清單中所參考資源的列舉值指標。</span><span class="sxs-lookup"><span data-stu-id="353c3-103">Gets a pointer to an enumerator for the resources referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="353c3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumManifestResources (  
    [in, out] HCORENUM         *phEnum,   
    [out] mdManifestResource   rManifestResources[],   
    [in]  ULONG                cMax,   
    [out] ULONG                *pcTokens  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="353c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="353c3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="353c3-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="353c3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="353c3-107">第一次呼叫 `EnumManifestResources` 方法時，這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="353c3-107">This must be a null value when the `EnumManifestResources` method is called for the first time.</span></span>  
  
 `rManifestResources`  
 <span data-ttu-id="353c3-108">脫銷用來儲存 `mdManifestResource` 元資料標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="353c3-108">[out] The array used to store the `mdManifestResource` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="353c3-109">在可以放在 `rManifestResources`中的 `mdManifestResource` token 的數目上限。</span><span class="sxs-lookup"><span data-stu-id="353c3-109">[in] The maximum number of `mdManifestResource` tokens that can be placed in `rManifestResources`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="353c3-110">脫銷實際放入 `rManifestResources`的 `mdManifestResource` token 數目。</span><span class="sxs-lookup"><span data-stu-id="353c3-110">[out] The number of `mdManifestResource` tokens actually placed in `rManifestResources`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353c3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="353c3-111">Return Value</span></span>  
  
|<span data-ttu-id="353c3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="353c3-112">HRESULT</span></span>|<span data-ttu-id="353c3-113">描述</span><span class="sxs-lookup"><span data-stu-id="353c3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="353c3-114">已成功傳回 `EnumManifestResources`。</span><span class="sxs-lookup"><span data-stu-id="353c3-114">`EnumManifestResources` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="353c3-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="353c3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="353c3-116">在此情況下，`pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="353c3-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="353c3-117">需求</span><span class="sxs-lookup"><span data-stu-id="353c3-117">Requirements</span></span>  
 <span data-ttu-id="353c3-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="353c3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353c3-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="353c3-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="353c3-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="353c3-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="353c3-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353c3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353c3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="353c3-122">See also</span></span>

- [<span data-ttu-id="353c3-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="353c3-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
