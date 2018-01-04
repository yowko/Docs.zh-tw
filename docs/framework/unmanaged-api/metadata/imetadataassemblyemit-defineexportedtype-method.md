---
title: "IMetaDataAssemblyEmit::DefineExportedType 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.DefineExportedType
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59aae188e404ebc717a140fb7918e3fbf69f3f70
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="aaabe-102">IMetaDataAssemblyEmit::DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="aaabe-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="aaabe-103">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="aaabe-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaabe-104">語法</span><span class="sxs-lookup"><span data-stu-id="aaabe-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aaabe-105">參數</span><span class="sxs-lookup"><span data-stu-id="aaabe-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="aaabe-106">[in]若要匯出的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="aaabe-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="aaabe-107">1.1 版的 common language runtime 所匯出的類型名稱必須完全符合指定的名稱為`TypeDef`類型。</span><span class="sxs-lookup"><span data-stu-id="aaabe-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="aaabe-108">[in]指定匯出的類型，實作語彙基元。</span><span class="sxs-lookup"><span data-stu-id="aaabe-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="aaabe-109">有效的值和其相關聯的意義如下：</span><span class="sxs-lookup"><span data-stu-id="aaabe-109">The valid values and their associated meanings are:</span></span>  
  
-   <span data-ttu-id="aaabe-110">`mdFile`類型會實作這個組件內不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="aaabe-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
-   <span data-ttu-id="aaabe-111">`mdAssemblyRef`類型是在不同的組件中的實作。</span><span class="sxs-lookup"><span data-stu-id="aaabe-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
-   <span data-ttu-id="aaabe-112">`mdExportedTYpe`類型被巢狀其他型別。</span><span class="sxs-lookup"><span data-stu-id="aaabe-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
-   <span data-ttu-id="aaabe-113">`mdFileNil`此類型是在相同的資訊清單檔案中，不是巢狀的類型。</span><span class="sxs-lookup"><span data-stu-id="aaabe-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="aaabe-114">[in]指定要匯出類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="aaabe-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="aaabe-115">在輸入此值`TypeDef`資料表中的檔案實作的型別，而且該檔案位於這個組件時，才會相關。</span><span class="sxs-lookup"><span data-stu-id="aaabe-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="aaabe-116">[in]位元組合[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)定義匯出的類型的屬性設定的列舉值。</span><span class="sxs-lookup"><span data-stu-id="aaabe-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="aaabe-117">[out]指出所匯出的類型傳回的中繼資料語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="aaabe-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaabe-118">備註</span><span class="sxs-lookup"><span data-stu-id="aaabe-118">Remarks</span></span>  
 <span data-ttu-id="aaabe-119">`ExportedType`必須為這個組件由每個類型，它實作於以外含有資訊清單模組定義中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="aaabe-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaabe-120">需求</span><span class="sxs-lookup"><span data-stu-id="aaabe-120">Requirements</span></span>  
 <span data-ttu-id="aaabe-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aaabe-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaabe-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aaabe-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aaabe-123">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="aaabe-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aaabe-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaabe-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaabe-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="aaabe-125">See Also</span></span>  
 [<span data-ttu-id="aaabe-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="aaabe-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
