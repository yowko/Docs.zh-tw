---
title: IMetaDataAssemblyImport::GetManifestResourceProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5bad338777db2097ed72ce327f42fde0f0db58e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693713"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="f1025-102">IMetaDataAssemblyImport::GetManifestResourceProps 方法</span><span class="sxs-lookup"><span data-stu-id="f1025-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>
<span data-ttu-id="f1025-103">取得具有指定之中繼資料簽章的資訊清單資源的屬性集。</span><span class="sxs-lookup"><span data-stu-id="f1025-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1025-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1025-104">Syntax</span></span>  
  
```  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] mdToken              *ptkImplementation,   
    [out] DWORD                *pdwOffset,   
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1025-105">參數</span><span class="sxs-lookup"><span data-stu-id="f1025-105">Parameters</span></span>  
 `mdmr`  
 <span data-ttu-id="f1025-106">[in]`mdManifestResource`語彙基元，表示要為其取得屬性的資源。</span><span class="sxs-lookup"><span data-stu-id="f1025-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="f1025-107">[out]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="f1025-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f1025-108">[in]大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="f1025-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f1025-109">[out]中實際傳回的寬字元數目的指標`szName`。</span><span class="sxs-lookup"><span data-stu-id="f1025-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="f1025-110">[out]指標`mdFile`語彙基元或`mdAssemblyRef`分別代表檔案或組件，包含資源的權杖。</span><span class="sxs-lookup"><span data-stu-id="f1025-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="f1025-111">[out]指定的資源檔中的開頭的位移值的指標。</span><span class="sxs-lookup"><span data-stu-id="f1025-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="f1025-112">[out]指標，描述套用至資源的中繼資料的旗標。</span><span class="sxs-lookup"><span data-stu-id="f1025-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="f1025-113">旗標值是由一或多個組成[CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="f1025-113">The flags value is a combination of one or more [CorManifestResourceFlags](../../../../docs/framework/unmanaged-api/metadata/cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1025-114">需求</span><span class="sxs-lookup"><span data-stu-id="f1025-114">Requirements</span></span>  
 <span data-ttu-id="f1025-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1025-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1025-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1025-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1025-117">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f1025-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1025-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1025-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1025-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1025-119">See also</span></span>
- [<span data-ttu-id="f1025-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="f1025-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
