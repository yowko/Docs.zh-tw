---
title: IMetaDataEmit::TranslateSigWithScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c571e37d87ffd136687452dc80a823b8ddbe3359
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782066"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="a627c-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="a627c-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="a627c-103">組件匯入目前的範圍，並取得新的中繼資料簽章為合併的範圍。</span><span class="sxs-lookup"><span data-stu-id="a627c-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a627c-104">語法</span><span class="sxs-lookup"><span data-stu-id="a627c-104">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a627c-105">參數</span><span class="sxs-lookup"><span data-stu-id="a627c-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="a627c-106">[in]匯入組件 （其中會定義簽章） 介面。</span><span class="sxs-lookup"><span data-stu-id="a627c-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="a627c-107">[in]組件雜湊的 blob。</span><span class="sxs-lookup"><span data-stu-id="a627c-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="a627c-108">[in]中的位元組計數`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="a627c-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="a627c-109">[in]匯入中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="a627c-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="a627c-110">[in]要匯入簽章。</span><span class="sxs-lookup"><span data-stu-id="a627c-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="a627c-111">[in]大小，以位元組為單位的`pbSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="a627c-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="a627c-112">[in]匯出組件的介面。</span><span class="sxs-lookup"><span data-stu-id="a627c-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="a627c-113">[in]匯出中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="a627c-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="a627c-114">[out]要保存已翻譯的簽章 blob 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a627c-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="a627c-115">[in]容量，以位元組為單位的`pvTranslatedSig`。</span><span class="sxs-lookup"><span data-stu-id="a627c-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="a627c-116">[out]已翻譯的簽章中的實際位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a627c-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a627c-117">需求</span><span class="sxs-lookup"><span data-stu-id="a627c-117">Requirements</span></span>  
 <span data-ttu-id="a627c-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a627c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a627c-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a627c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a627c-120">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a627c-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a627c-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a627c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a627c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a627c-122">See also</span></span>

- [<span data-ttu-id="a627c-123">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a627c-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="a627c-124">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="a627c-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="a627c-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a627c-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a627c-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a627c-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="a627c-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a627c-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
