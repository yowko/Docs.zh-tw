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
ms.openlocfilehash: 15b58e01d4ce99f19f510c760819471b84380b45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177764"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="6f630-102">IMetaDataAssemblyImport::GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="6f630-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="6f630-103">使用指定的中繼資料簽名獲取匯出類型的屬性集。</span><span class="sxs-lookup"><span data-stu-id="6f630-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f630-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f630-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="6f630-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f630-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="6f630-106">[在]表示`mdExportedType`匯出類型的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="6f630-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="6f630-107">[出]匯出類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f630-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6f630-108">[在]的大小（以寬字元表示`szName`）</span><span class="sxs-lookup"><span data-stu-id="6f630-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="6f630-109">[出]實際返回的寬字元數`szName`</span><span class="sxs-lookup"><span data-stu-id="6f630-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="6f630-110">[出]包含`mdFile`或`mdAssemblyRef`允許訪問`mdExportedType`匯出類型的屬性的 中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="6f630-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="6f630-111">[出]指向表示檔中類型的`mdTypeDef`權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="6f630-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="6f630-112">[出]指向用於應用於匯出類型的中繼資料的標誌的指標。</span><span class="sxs-lookup"><span data-stu-id="6f630-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="6f630-113">標誌值可以是一個或多個[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="6f630-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f630-114">需求</span><span class="sxs-lookup"><span data-stu-id="6f630-114">Requirements</span></span>  
 <span data-ttu-id="6f630-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f630-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f630-116">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="6f630-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f630-117">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6f630-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f630-118">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f630-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f630-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f630-119">See also</span></span>

- [<span data-ttu-id="6f630-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="6f630-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
