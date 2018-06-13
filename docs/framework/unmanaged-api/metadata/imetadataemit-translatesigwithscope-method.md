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
ms.openlocfilehash: 0ddaddbbd050dc079fcf20551e90c895d2f4ef59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446339"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="79eee-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="79eee-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="79eee-103">組件匯入目前的範圍，並取得新的中繼資料簽章為合併的範圍。</span><span class="sxs-lookup"><span data-stu-id="79eee-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79eee-104">語法</span><span class="sxs-lookup"><span data-stu-id="79eee-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="79eee-105">參數</span><span class="sxs-lookup"><span data-stu-id="79eee-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="79eee-106">[in]匯入組件 （其中簽章定義） 的介面。</span><span class="sxs-lookup"><span data-stu-id="79eee-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="79eee-107">[in]組件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="79eee-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="79eee-108">[in]中的位元組計數`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="79eee-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="79eee-109">[in]匯入中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="79eee-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="79eee-110">[in]要匯入簽章。</span><span class="sxs-lookup"><span data-stu-id="79eee-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="79eee-111">[in]大小，以位元組為單位的`pbSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="79eee-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="79eee-112">[in]匯出組件介面。</span><span class="sxs-lookup"><span data-stu-id="79eee-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="79eee-113">[in]匯出中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="79eee-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="79eee-114">[out]要保存已翻譯的簽章 blob 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="79eee-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="79eee-115">[in]容量，以位元組為單位的`pvTranslatedSig`。</span><span class="sxs-lookup"><span data-stu-id="79eee-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="79eee-116">[out]翻譯的簽章中的實際位元組數目。</span><span class="sxs-lookup"><span data-stu-id="79eee-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79eee-117">需求</span><span class="sxs-lookup"><span data-stu-id="79eee-117">Requirements</span></span>  
 <span data-ttu-id="79eee-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79eee-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79eee-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="79eee-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79eee-120">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="79eee-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79eee-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79eee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79eee-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79eee-122">See Also</span></span>  
 [<span data-ttu-id="79eee-123">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="79eee-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [<span data-ttu-id="79eee-124">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="79eee-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 [<span data-ttu-id="79eee-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="79eee-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="79eee-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="79eee-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="79eee-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="79eee-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
