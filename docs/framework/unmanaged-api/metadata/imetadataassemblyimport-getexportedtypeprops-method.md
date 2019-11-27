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
ms.openlocfilehash: 82302124828a2dab73b445128d7d847e112edd36
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448215"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="8c05e-102">IMetaDataAssemblyImport::GetExportedTypeProps 方法</span><span class="sxs-lookup"><span data-stu-id="8c05e-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>
<span data-ttu-id="8c05e-103">取得具有指定的中繼資料簽章之已匯出類型的屬性集。</span><span class="sxs-lookup"><span data-stu-id="8c05e-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c05e-104">語法</span><span class="sxs-lookup"><span data-stu-id="8c05e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8c05e-105">參數</span><span class="sxs-lookup"><span data-stu-id="8c05e-105">Parameters</span></span>  
 `mdct`  
 <span data-ttu-id="8c05e-106">在表示已匯出類型的 `mdExportedType` 元資料標記。</span><span class="sxs-lookup"><span data-stu-id="8c05e-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="8c05e-107">脫銷匯出之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="8c05e-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8c05e-108">在`szName`的大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="8c05e-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="8c05e-109">脫銷`szName` 中實際傳回的寬字元數</span><span class="sxs-lookup"><span data-stu-id="8c05e-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="8c05e-110">脫銷`mdFile`、`mdAssemblyRef`或 `mdExportedType` 元資料標記，其中包含或允許存取匯出類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="8c05e-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="8c05e-111">脫銷`mdTypeDef` token 的指標，表示檔案中的類型。</span><span class="sxs-lookup"><span data-stu-id="8c05e-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="8c05e-112">脫銷旗標的指標，描述套用至已匯出類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="8c05e-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="8c05e-113">Flags 值可以是一或多個[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)值。</span><span class="sxs-lookup"><span data-stu-id="8c05e-113">The flags value can be one or more [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c05e-114">需求</span><span class="sxs-lookup"><span data-stu-id="8c05e-114">Requirements</span></span>  
 <span data-ttu-id="8c05e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8c05e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c05e-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8c05e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c05e-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="8c05e-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c05e-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c05e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c05e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c05e-119">See also</span></span>

- [<span data-ttu-id="8c05e-120">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="8c05e-120">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
