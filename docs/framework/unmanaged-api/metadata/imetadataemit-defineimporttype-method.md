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
ms.openlocfilehash: 5b4b0682b2bddff96cb3d720900ed3aa39f06f9d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431846"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="fa37c-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="fa37c-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="fa37c-103">建立定義于目前範圍外之指定類型的參考，並定義該參考的 token。</span><span class="sxs-lookup"><span data-stu-id="fa37c-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa37c-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa37c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="fa37c-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa37c-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="fa37c-106">在[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)介面，表示從中匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="fa37c-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="fa37c-107">在陣列，其中包含 `pAssemImport`所指定之元件的雜湊。</span><span class="sxs-lookup"><span data-stu-id="fa37c-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="fa37c-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="fa37c-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="fa37c-109">在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從中匯入目標型別的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="fa37c-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="fa37c-110">在指定目標型別的 `mdTypeDef` token。</span><span class="sxs-lookup"><span data-stu-id="fa37c-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="fa37c-111">在[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示要匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="fa37c-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="fa37c-112">脫銷在類型參考的目前範圍中定義的 `mdTypeRef` token。</span><span class="sxs-lookup"><span data-stu-id="fa37c-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa37c-113">備註</span><span class="sxs-lookup"><span data-stu-id="fa37c-113">Remarks</span></span>  
 <span data-ttu-id="fa37c-114">在呼叫[IMetaDataEmit：:D efineimportmember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)方法之前，您可以使用 `DefineImportType` 方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。</span><span class="sxs-lookup"><span data-stu-id="fa37c-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa37c-115">需求</span><span class="sxs-lookup"><span data-stu-id="fa37c-115">Requirements</span></span>  
 <span data-ttu-id="fa37c-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa37c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa37c-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fa37c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa37c-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="fa37c-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fa37c-119">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa37c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa37c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa37c-120">See also</span></span>

- [<span data-ttu-id="fa37c-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fa37c-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fa37c-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fa37c-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
