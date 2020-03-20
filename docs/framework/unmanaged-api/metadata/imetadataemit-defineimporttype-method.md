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
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177686"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="dd6a8-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="dd6a8-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="dd6a8-103">創建對在當前作用域之外定義的指定類型的引用，並為該引用定義權杖。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd6a8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dd6a8-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd6a8-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="dd6a8-106">[在][IMetaDataAssemblyImport 介面](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)，表示從中導入目標型別的程式集。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="dd6a8-107">[在]包含 的陣列，其中包含 由 指定的`pAssemImport`程式集的雜湊值。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="dd6a8-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="dd6a8-109">[在][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)介面，表示從中導入目標型別的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="dd6a8-110">[在]指定`mdTypeDef`目標型別的權杖。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="dd6a8-111">[在][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)介面，表示將目標型別導入到的程式集。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="dd6a8-112">[出]類型`mdTypeRef`引用的當前作用域中定義的權杖。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd6a8-113">備註</span><span class="sxs-lookup"><span data-stu-id="dd6a8-113">Remarks</span></span>  
 <span data-ttu-id="dd6a8-114">在調用[IMetaDataEmit：:DefineImportI成員](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)方法之前，可以使用`DefineImportType`該方法為成員的父類或父介面在當前作用域中創建類型引用。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd6a8-115">需求</span><span class="sxs-lookup"><span data-stu-id="dd6a8-115">Requirements</span></span>  
 <span data-ttu-id="dd6a8-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd6a8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd6a8-117">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="dd6a8-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd6a8-118">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dd6a8-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd6a8-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd6a8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6a8-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd6a8-120">See also</span></span>

- [<span data-ttu-id="dd6a8-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="dd6a8-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dd6a8-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="dd6a8-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
