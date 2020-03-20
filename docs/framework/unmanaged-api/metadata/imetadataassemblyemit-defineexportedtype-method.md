---
title: IMetaDataAssemblyEmit::DefineExportedType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 388f227377ddf73fe1297e1c777bb1c0607c13d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177873"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="1911d-102">IMetaDataAssemblyEmit::DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="1911d-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="1911d-103">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1911d-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1911d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1911d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1911d-105">參數</span><span class="sxs-lookup"><span data-stu-id="1911d-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="1911d-106">[在]要匯出的類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="1911d-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="1911d-107">對於通用語言運行時的版本 1.1，匯出類型的名稱必須與 類型中`TypeDef`給出的名稱完全符合。</span><span class="sxs-lookup"><span data-stu-id="1911d-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="1911d-108">[在]指定匯出類型的實現位置的權杖。</span><span class="sxs-lookup"><span data-stu-id="1911d-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="1911d-109">有效值及其相關含義包括：</span><span class="sxs-lookup"><span data-stu-id="1911d-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="1911d-110">`mdFile`該類型在此程式集中的其他檔中實現。</span><span class="sxs-lookup"><span data-stu-id="1911d-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="1911d-111">`mdAssemblyRef`該類型在不同的程式集中實現。</span><span class="sxs-lookup"><span data-stu-id="1911d-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="1911d-112">`mdExportedTYpe`類型嵌套在某種其他類型中。</span><span class="sxs-lookup"><span data-stu-id="1911d-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="1911d-113">`mdFileNil`類型與清單位於同一檔中，不是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="1911d-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="1911d-114">[在]指定要匯出的類型的中繼資料的權杖。</span><span class="sxs-lookup"><span data-stu-id="1911d-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="1911d-115">此值在檔中實現該類型的`TypeDef`表中輸入，並且僅當該檔位於此程式集中時才相關。</span><span class="sxs-lookup"><span data-stu-id="1911d-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="1911d-116">[在][CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)枚舉值的位組合，用於定義匯出類型的屬性設置。</span><span class="sxs-lookup"><span data-stu-id="1911d-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="1911d-117">[出]指向返回的中繼資料權杖的指標，指示匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="1911d-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1911d-118">備註</span><span class="sxs-lookup"><span data-stu-id="1911d-118">Remarks</span></span>  
 <span data-ttu-id="1911d-119">必須`ExportedType`為此程式集公開的並且在包含清單的模組以外的模組中實現的每一種類型定義元資料結構。</span><span class="sxs-lookup"><span data-stu-id="1911d-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1911d-120">需求</span><span class="sxs-lookup"><span data-stu-id="1911d-120">Requirements</span></span>  
 <span data-ttu-id="1911d-121">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1911d-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1911d-122">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="1911d-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1911d-123">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="1911d-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1911d-124">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1911d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1911d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1911d-125">See also</span></span>

- [<span data-ttu-id="1911d-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="1911d-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
