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
ms.openlocfilehash: edce5cb93b770fb5730e5a06633ffffacf332f7a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004684"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="4985b-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="4985b-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="4985b-103">建立定義于目前範圍外之指定類型的參考，並定義該參考的 token。</span><span class="sxs-lookup"><span data-stu-id="4985b-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4985b-104">語法</span><span class="sxs-lookup"><span data-stu-id="4985b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4985b-105">參數</span><span class="sxs-lookup"><span data-stu-id="4985b-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="4985b-106">在[IMetaDataAssemblyImport](imetadataassemblyimport-interface.md)介面，表示從中匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="4985b-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="4985b-107">在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="4985b-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="4985b-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="4985b-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="4985b-109">在[IMetaDataImport](imetadataimport-interface.md)介面，表示從中匯入目標型別的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="4985b-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="4985b-110">在`mdTypeDef`指定目標型別的 token。</span><span class="sxs-lookup"><span data-stu-id="4985b-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="4985b-111">在[IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md)介面，表示要匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="4985b-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="4985b-112">脫銷`mdTypeRef`在類型參考的目前範圍中定義的 token。</span><span class="sxs-lookup"><span data-stu-id="4985b-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4985b-113">備註</span><span class="sxs-lookup"><span data-stu-id="4985b-113">Remarks</span></span>  
 <span data-ttu-id="4985b-114">呼叫[IMetaDataEmit：:D efineimportmember](imetadataemit-defineimportmember-method.md)方法之前，您可以使用 `DefineImportType` 方法，針對成員的父類別或父介面，在目前的範圍中建立類型參考。</span><span class="sxs-lookup"><span data-stu-id="4985b-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4985b-115">需求</span><span class="sxs-lookup"><span data-stu-id="4985b-115">Requirements</span></span>  
 <span data-ttu-id="4985b-116">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4985b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4985b-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="4985b-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4985b-118">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="4985b-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4985b-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4985b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4985b-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4985b-120">See also</span></span>

- [<span data-ttu-id="4985b-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="4985b-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4985b-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="4985b-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
