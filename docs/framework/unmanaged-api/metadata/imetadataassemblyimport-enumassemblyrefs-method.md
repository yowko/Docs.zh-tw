---
title: "IMetaDataAssemblyImport::EnumAssemblyRefs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.EnumAssemblyRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 24a289ed42a99cd26c7829d9a5789ac3027026c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="52c65-102">IMetaDataAssemblyImport::EnumAssemblyRefs 方法</span><span class="sxs-lookup"><span data-stu-id="52c65-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>
<span data-ttu-id="52c65-103">列舉`mdAssemblyRef`組件資訊清單中所定義的執行個體。</span><span class="sxs-lookup"><span data-stu-id="52c65-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52c65-104">語法</span><span class="sxs-lookup"><span data-stu-id="52c65-104">Syntax</span></span>  
  
```  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,   
    [out]     mdAssemblyRef   rAssemblyRefs[],   
    [in]      ULONG           cMax,   
    [out]     ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52c65-105">參數</span><span class="sxs-lookup"><span data-stu-id="52c65-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="52c65-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="52c65-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="52c65-107">這必須是 null 值時`EnumAssemblyRefs`第一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="52c65-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="52c65-108">[out]列舉`mdAssemblyRef`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52c65-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="52c65-109">[in]可以放入權杖的最大數目`rAssemblyRefs`陣列。</span><span class="sxs-lookup"><span data-stu-id="52c65-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="52c65-110">[out]語彙基元數目實際置於`rAssemblyRefs`。</span><span class="sxs-lookup"><span data-stu-id="52c65-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52c65-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="52c65-111">Return Value</span></span>  
  
|<span data-ttu-id="52c65-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="52c65-112">HRESULT</span></span>|<span data-ttu-id="52c65-113">說明</span><span class="sxs-lookup"><span data-stu-id="52c65-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="52c65-114">`EnumAssemblyRefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="52c65-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="52c65-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="52c65-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="52c65-116">在此情況下，`pcTokens`設為零。</span><span class="sxs-lookup"><span data-stu-id="52c65-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="52c65-117">需求</span><span class="sxs-lookup"><span data-stu-id="52c65-117">Requirements</span></span>  
 <span data-ttu-id="52c65-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52c65-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c65-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="52c65-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="52c65-120">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="52c65-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="52c65-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c65-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c65-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52c65-122">See Also</span></span>  
 [<span data-ttu-id="52c65-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="52c65-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
