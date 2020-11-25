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
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723242"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="c8511-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="c8511-102">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="c8511-103">建立在目前範圍之外定義之指定型別的參考，並定義該參考的權杖。</span><span class="sxs-lookup"><span data-stu-id="c8511-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8511-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8511-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c8511-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8511-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="c8511-106">在 [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) 介面，表示匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="c8511-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c8511-107">在陣列，其中包含所指定之元件的雜湊 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="c8511-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c8511-108">[in] `pbHashValue` 陣列中的位元組數。</span><span class="sxs-lookup"><span data-stu-id="c8511-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="c8511-109">在 [IMetaDataImport](imetadataimport-interface.md) 介面，表示要從中匯入目標型別的中繼資料範圍。</span><span class="sxs-lookup"><span data-stu-id="c8511-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="c8511-110">在 `mdTypeDef` 指定目標型別的標記。</span><span class="sxs-lookup"><span data-stu-id="c8511-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="c8511-111">在 [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) 介面，表示要匯入目標型別的元件。</span><span class="sxs-lookup"><span data-stu-id="c8511-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="c8511-112">擴展在 `mdTypeRef` 目前範圍中針對型別參考定義的標記。</span><span class="sxs-lookup"><span data-stu-id="c8511-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8511-113">備註</span><span class="sxs-lookup"><span data-stu-id="c8511-113">Remarks</span></span>  

 <span data-ttu-id="c8511-114">在呼叫 [IMetaDataEmit：:D efineimportmember](imetadataemit-defineimportmember-method.md) 方法之前，您可以使用方法， `DefineImportType` 在目前的範圍中，為成員的父類別或父介面建立型別參考。</span><span class="sxs-lookup"><span data-stu-id="c8511-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8511-115">需求</span><span class="sxs-lookup"><span data-stu-id="c8511-115">Requirements</span></span>  

 <span data-ttu-id="c8511-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8511-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8511-117">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c8511-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8511-118">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c8511-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8511-119">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8511-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8511-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8511-120">See also</span></span>

- [<span data-ttu-id="c8511-121">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c8511-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c8511-122">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c8511-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
