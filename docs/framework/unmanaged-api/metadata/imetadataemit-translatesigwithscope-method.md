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
ms.openlocfilehash: 2662af41fbd2cdc3ce8a6df1e036dfc5b22ff6a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175547"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="79b82-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="79b82-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="79b82-103">將程式集導入當前作用域，並為合併作用域獲取新的中繼資料簽名。</span><span class="sxs-lookup"><span data-stu-id="79b82-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79b82-104">語法</span><span class="sxs-lookup"><span data-stu-id="79b82-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="79b82-105">參數</span><span class="sxs-lookup"><span data-stu-id="79b82-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="79b82-106">[在]導入程式集的介面（定義簽名的位置）。</span><span class="sxs-lookup"><span data-stu-id="79b82-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="79b82-107">[在]程式集的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="79b82-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="79b82-108">[在]中的`pbHashValue`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="79b82-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="79b82-109">[在]導入中繼資料作用域的介面。</span><span class="sxs-lookup"><span data-stu-id="79b82-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="79b82-110">[在]要導入的簽名。</span><span class="sxs-lookup"><span data-stu-id="79b82-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="79b82-111">[在]的大小（以位元組為單位）的大小`pbSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="79b82-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="79b82-112">[在]匯出程式集的介面。</span><span class="sxs-lookup"><span data-stu-id="79b82-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="79b82-113">[在]匯出中繼資料作用域的介面。</span><span class="sxs-lookup"><span data-stu-id="79b82-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="79b82-114">[出]用於保存已翻譯的簽名 blob 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="79b82-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="79b82-115">[在]的容量（以位元組為單位`pvTranslatedSig`）。</span><span class="sxs-lookup"><span data-stu-id="79b82-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="79b82-116">[出]翻譯簽名中的實際位元組數。</span><span class="sxs-lookup"><span data-stu-id="79b82-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79b82-117">需求</span><span class="sxs-lookup"><span data-stu-id="79b82-117">Requirements</span></span>  
 <span data-ttu-id="79b82-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="79b82-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79b82-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="79b82-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="79b82-120">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="79b82-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="79b82-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79b82-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79b82-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79b82-122">See also</span></span>

- [<span data-ttu-id="79b82-123">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="79b82-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="79b82-124">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="79b82-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="79b82-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="79b82-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="79b82-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="79b82-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="79b82-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="79b82-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
