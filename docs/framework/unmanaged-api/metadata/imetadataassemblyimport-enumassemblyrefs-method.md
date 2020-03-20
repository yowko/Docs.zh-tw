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
ms.openlocfilehash: 6a4489d094974eb872b39824ceb185b0cbe48625
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177820"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="4ef50-102">IMetaDataAssemblyImport::EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4ef50-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="4ef50-103">枚舉程式集`mdAssemblyRef`清單中定義的實例。</span><span class="sxs-lookup"><span data-stu-id="4ef50-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef50-104">語法</span><span class="sxs-lookup"><span data-stu-id="4ef50-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ef50-105">參數</span><span class="sxs-lookup"><span data-stu-id="4ef50-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4ef50-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="4ef50-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4ef50-107">當首次調用該方法時，`EnumAssemblyRefs`這必須是 null 值。</span><span class="sxs-lookup"><span data-stu-id="4ef50-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="4ef50-108">[出]中繼資料權杖的`mdAssemblyRef`枚舉。</span><span class="sxs-lookup"><span data-stu-id="4ef50-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4ef50-109">[在]可放置在`rAssemblyRefs`陣列中的最大權杖數。</span><span class="sxs-lookup"><span data-stu-id="4ef50-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4ef50-110">[出]實際放置在 中的`rAssemblyRefs`權杖數。</span><span class="sxs-lookup"><span data-stu-id="4ef50-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ef50-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4ef50-111">Return Value</span></span>  
  
|<span data-ttu-id="4ef50-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ef50-112">HRESULT</span></span>|<span data-ttu-id="4ef50-113">描述</span><span class="sxs-lookup"><span data-stu-id="4ef50-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4ef50-114">`EnumAssemblyRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="4ef50-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4ef50-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="4ef50-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="4ef50-116">在這種情況下，`pcTokens`設置為零。</span><span class="sxs-lookup"><span data-stu-id="4ef50-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ef50-117">需求</span><span class="sxs-lookup"><span data-stu-id="4ef50-117">Requirements</span></span>  
 <span data-ttu-id="4ef50-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4ef50-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ef50-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="4ef50-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4ef50-120">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4ef50-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4ef50-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ef50-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef50-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ef50-122">See also</span></span>

- [<span data-ttu-id="4ef50-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="4ef50-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
