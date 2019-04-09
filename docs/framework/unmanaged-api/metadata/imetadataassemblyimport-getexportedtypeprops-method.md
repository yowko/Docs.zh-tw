---
title: IMetaDataAssemblyImport::GetExportedTypeProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91b1e4469f07954dc433769911c78d72bb3c36cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096146"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="34b64-102">IMetaDataAssemblyImport::GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="34b64-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="34b64-103">取得具有指定之中繼資料簽章之匯出類型的屬性集。</span><span class="sxs-lookup"><span data-stu-id="34b64-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b64-104">語法</span><span class="sxs-lookup"><span data-stu-id="34b64-104">Syntax</span></span>  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34b64-105">參數</span><span class="sxs-lookup"><span data-stu-id="34b64-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="34b64-106">[in]`mdExportedType`中繼資料語彙基元，表示匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="34b64-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="34b64-107">[out]匯出的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="34b64-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="34b64-108">[in]大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="34b64-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="34b64-109">[out]中實際傳回的寬字元數目</span><span class="sxs-lookup"><span data-stu-id="34b64-109">[out] The number of wide characters actually returned in</span></span> `szName`  
  
 `ptkImplementation`  
 <span data-ttu-id="34b64-110">[out]`mdFile`， `mdAssemblyRef`，或`mdExportedType`包含或允許匯出的類型的屬性存取的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="34b64-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="34b64-111">[out]指標`mdTypeDef`語彙基元，表示檔案中的類型。</span><span class="sxs-lookup"><span data-stu-id="34b64-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="34b64-112">[out]指標，描述套用至匯出的型別中繼資料的旗標。</span><span class="sxs-lookup"><span data-stu-id="34b64-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="34b64-113">旗標值可以是一或多個[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="34b64-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34b64-114">需求</span><span class="sxs-lookup"><span data-stu-id="34b64-114">Requirements</span></span>  
 <span data-ttu-id="34b64-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34b64-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b64-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="34b64-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34b64-117">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="34b64-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="34b64-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="34b64-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34b64-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34b64-119">See also</span></span>

- [<span data-ttu-id="34b64-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="34b64-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
