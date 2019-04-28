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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91e253669b9f51e7c1d600ba11f13a9ce67fb58a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905108"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="329a1-102">IMetaDataAssemblyImport::EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="329a1-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="329a1-103">列舉`mdAssemblyRef`組件資訊清單中所定義的執行個體。</span><span class="sxs-lookup"><span data-stu-id="329a1-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="329a1-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="329a1-105">參數</span><span class="sxs-lookup"><span data-stu-id="329a1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="329a1-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="329a1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="329a1-107">這必須是 null 值時`EnumAssemblyRefs`第一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="329a1-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="329a1-108">[out]列舉`mdAssemblyRef`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="329a1-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="329a1-109">[in]可以放入權杖的最大數目`rAssemblyRefs`陣列。</span><span class="sxs-lookup"><span data-stu-id="329a1-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="329a1-110">[out]Token 的數目會實際放在`rAssemblyRefs`。</span><span class="sxs-lookup"><span data-stu-id="329a1-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="329a1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="329a1-111">Return Value</span></span>  
  
|<span data-ttu-id="329a1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="329a1-112">HRESULT</span></span>|<span data-ttu-id="329a1-113">描述</span><span class="sxs-lookup"><span data-stu-id="329a1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="329a1-114">`EnumAssemblyRefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="329a1-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="329a1-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="329a1-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="329a1-116">在此情況下，`pcTokens`設為零。</span><span class="sxs-lookup"><span data-stu-id="329a1-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="329a1-117">需求</span><span class="sxs-lookup"><span data-stu-id="329a1-117">Requirements</span></span>  
 <span data-ttu-id="329a1-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="329a1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="329a1-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="329a1-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="329a1-120">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="329a1-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="329a1-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="329a1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329a1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="329a1-122">See also</span></span>

- [<span data-ttu-id="329a1-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="329a1-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
