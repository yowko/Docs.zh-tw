---
title: IMetaDataAssemblyImport::EnumAssemblyRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 06b81615565a04db7d6cfef4da9b5372a85afd68
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450341"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="5cb82-102">IMetaDataAssemblyImport::EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="5cb82-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="5cb82-103">列舉在組件資訊清單中定義的 `mdAssemblyRef` 實例。</span><span class="sxs-lookup"><span data-stu-id="5cb82-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cb82-104">語法</span><span class="sxs-lookup"><span data-stu-id="5cb82-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cb82-105">參數</span><span class="sxs-lookup"><span data-stu-id="5cb82-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5cb82-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="5cb82-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5cb82-107">第一次呼叫 `EnumAssemblyRefs` 方法時，這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="5cb82-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="5cb82-108">脫銷`mdAssemblyRef` 元資料標記的列舉。</span><span class="sxs-lookup"><span data-stu-id="5cb82-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5cb82-109">在可以放在 `rAssemblyRefs` 陣列中的標記數目上限。</span><span class="sxs-lookup"><span data-stu-id="5cb82-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5cb82-110">脫銷實際放在 `rAssemblyRefs`中的權杖數目。</span><span class="sxs-lookup"><span data-stu-id="5cb82-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cb82-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="5cb82-111">Return Value</span></span>  
  
|<span data-ttu-id="5cb82-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cb82-112">HRESULT</span></span>|<span data-ttu-id="5cb82-113">描述</span><span class="sxs-lookup"><span data-stu-id="5cb82-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5cb82-114">已成功傳回 `EnumAssemblyRefs`。</span><span class="sxs-lookup"><span data-stu-id="5cb82-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5cb82-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="5cb82-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="5cb82-116">在此情況下，`pcTokens` 會設定為零。</span><span class="sxs-lookup"><span data-stu-id="5cb82-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5cb82-117">需求</span><span class="sxs-lookup"><span data-stu-id="5cb82-117">Requirements</span></span>  
 <span data-ttu-id="5cb82-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5cb82-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cb82-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="5cb82-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cb82-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="5cb82-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5cb82-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cb82-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb82-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cb82-122">See also</span></span>

- [<span data-ttu-id="5cb82-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="5cb82-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
