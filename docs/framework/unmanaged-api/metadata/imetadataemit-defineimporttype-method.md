---
title: IMetaDataEmit::DefineImportType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9ac7bc865371744f6742622243398a506607373c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469127"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="b64c1-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="b64c1-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="b64c1-103">建立指定的型別定義在目前的範圍之外，並定義該參考的語彙基元的參考。</span><span class="sxs-lookup"><span data-stu-id="b64c1-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="b64c1-104">Syntax</span></span>  
  
```  
HRESULT DefineImportType (   
    [in]  IMetaDataAssemblyImport  *pAssemImport,   
    [in]  const void               *pbHashValue,   
    [in]  ULONG                    cbHashValue,    
    [in]  IMetaDataImport          *pImport,   
    [in]  mdTypeDef                tdImport,   
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,   
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b64c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="b64c1-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="b64c1-106">[in][IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面，表示從其中匯入的目標類型的組件。</span><span class="sxs-lookup"><span data-stu-id="b64c1-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="b64c1-107">[in]陣列，其中包含所指定的組件的雜湊`pAssemImport`。</span><span class="sxs-lookup"><span data-stu-id="b64c1-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="b64c1-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="b64c1-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="b64c1-109">[in][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從其中匯入的目標類型的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="b64c1-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="b64c1-110">[in]`mdTypeDef`指定目標類型的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b64c1-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="b64c1-111">[in][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示組件匯入到其中的目標型別。</span><span class="sxs-lookup"><span data-stu-id="b64c1-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="b64c1-112">[out]`mdTypeRef`為型別參考目前範圍中定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b64c1-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64c1-113">備註</span><span class="sxs-lookup"><span data-stu-id="b64c1-113">Remarks</span></span>  
 <span data-ttu-id="b64c1-114">在呼叫之前[imetadataemit:: Defineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)方法，您可以使用`DefineImportType`方法用來建立型別參考，在目前範圍中，成員的父類別或父介面。</span><span class="sxs-lookup"><span data-stu-id="b64c1-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64c1-115">需求</span><span class="sxs-lookup"><span data-stu-id="b64c1-115">Requirements</span></span>  
 <span data-ttu-id="b64c1-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b64c1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64c1-117">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b64c1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b64c1-118">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b64c1-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b64c1-119">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64c1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64c1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b64c1-120">See also</span></span>
- [<span data-ttu-id="b64c1-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b64c1-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b64c1-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b64c1-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
