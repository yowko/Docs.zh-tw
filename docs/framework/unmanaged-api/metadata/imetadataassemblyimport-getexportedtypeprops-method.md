---
title: "IMetaDataAssemblyImport::GetExportedTypeProps 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc5bb8266814fc4f1333de78fce4b6af86893c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="2477d-102">IMetaDataAssemblyImport::GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="2477d-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="2477d-103">取得具有指定的中繼資料簽章之匯出類型的屬性集。</span><span class="sxs-lookup"><span data-stu-id="2477d-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2477d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2477d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2477d-105">參數</span><span class="sxs-lookup"><span data-stu-id="2477d-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="2477d-106">[in]`mdExportedType`中繼資料語彙基元，代表所匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="2477d-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="2477d-107">[out]匯出的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="2477d-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="2477d-108">[in]大小，以寬字元為單位的`szName`。</span><span class="sxs-lookup"><span data-stu-id="2477d-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="2477d-109">[out]中實際傳回的寬字元數目`szName`</span><span class="sxs-lookup"><span data-stu-id="2477d-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="2477d-110">[out]`mdFile`， `mdAssemblyRef`，或`mdExportedType`包含或允許匯出的類型的屬性存取的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2477d-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="2477d-111">[out]指標`mdTypeDef`表示檔案中的類型語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2477d-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="2477d-112">[out]描述套用至匯出的型別中繼資料的旗標指標。</span><span class="sxs-lookup"><span data-stu-id="2477d-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="2477d-113">旗標值可以是一個或多個[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="2477d-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2477d-114">需求</span><span class="sxs-lookup"><span data-stu-id="2477d-114">Requirements</span></span>  
 <span data-ttu-id="2477d-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2477d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2477d-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2477d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2477d-117">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2477d-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2477d-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2477d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2477d-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="2477d-119">See Also</span></span>  
 [<span data-ttu-id="2477d-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="2477d-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
