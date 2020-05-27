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
ms.openlocfilehash: 7ef6dbc46806febc6fba89b39a8b894377225c23
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003948"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="57738-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="57738-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="57738-103">將元件匯入到目前的範圍，並為合併的範圍取得新的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="57738-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57738-104">語法</span><span class="sxs-lookup"><span data-stu-id="57738-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="57738-105">參數</span><span class="sxs-lookup"><span data-stu-id="57738-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="57738-106">在匯入元件的介面（定義簽章的位置）。</span><span class="sxs-lookup"><span data-stu-id="57738-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="57738-107">在元件的雜湊 blob。</span><span class="sxs-lookup"><span data-stu-id="57738-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="57738-108">在中的位元組計數 `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="57738-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="57738-109">在匯入中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="57738-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="57738-110">在要匯入的簽章。</span><span class="sxs-lookup"><span data-stu-id="57738-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="57738-111">在的大小（以位元組為單位） `pbSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="57738-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="57738-112">在匯出元件的介面。</span><span class="sxs-lookup"><span data-stu-id="57738-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="57738-113">在用於匯出中繼資料範圍的介面。</span><span class="sxs-lookup"><span data-stu-id="57738-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="57738-114">脫銷保存已轉譯之簽章 blob 的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="57738-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="57738-115">在的容量（以位元組為單位） `pvTranslatedSig` 。</span><span class="sxs-lookup"><span data-stu-id="57738-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="57738-116">脫銷翻譯簽章中的實際位元組數。</span><span class="sxs-lookup"><span data-stu-id="57738-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57738-117">需求</span><span class="sxs-lookup"><span data-stu-id="57738-117">Requirements</span></span>  
 <span data-ttu-id="57738-118">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="57738-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57738-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="57738-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57738-120">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="57738-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57738-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57738-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57738-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57738-122">See also</span></span>

- [<span data-ttu-id="57738-123">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="57738-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="57738-124">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="57738-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="57738-125">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="57738-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="57738-126">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="57738-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="57738-127">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="57738-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
