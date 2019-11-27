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
ms.openlocfilehash: cea84f47a5289df4bc9c50381e18d7077b3b8dad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440469"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="db542-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="db542-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="db542-103">將元件匯入到目前的範圍，並為合併的範圍取得新的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="db542-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db542-104">語法</span><span class="sxs-lookup"><span data-stu-id="db542-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="db542-105">參數</span><span class="sxs-lookup"><span data-stu-id="db542-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="db542-106">在匯入元件的介面（定義簽章的位置）。</span><span class="sxs-lookup"><span data-stu-id="db542-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="db542-107">在元件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="db542-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="db542-108">在`pbHashValue`中的位元組計數。</span><span class="sxs-lookup"><span data-stu-id="db542-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="db542-109">在匯入中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="db542-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="db542-110">在要匯入的簽章。</span><span class="sxs-lookup"><span data-stu-id="db542-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="db542-111">在`pbSigBlob`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="db542-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="db542-112">在匯出元件的介面。</span><span class="sxs-lookup"><span data-stu-id="db542-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="db542-113">在用於匯出中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="db542-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="db542-114">脫銷保存已轉譯之簽章 blob 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="db542-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="db542-115">在`pvTranslatedSig`的容量（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="db542-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="db542-116">脫銷翻譯簽章中的實際位元組數。</span><span class="sxs-lookup"><span data-stu-id="db542-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db542-117">需求</span><span class="sxs-lookup"><span data-stu-id="db542-117">Requirements</span></span>  
 <span data-ttu-id="db542-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="db542-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db542-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="db542-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db542-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="db542-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db542-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db542-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db542-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db542-122">See also</span></span>

- [<span data-ttu-id="db542-123">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="db542-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="db542-124">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="db542-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="db542-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="db542-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="db542-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="db542-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="db542-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="db542-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
