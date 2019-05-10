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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5702fac139ba602828bb8722a1e3e25d6f1c58f6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625430"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="8016c-102">IMetaDataAssemblyEmit::DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="8016c-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>
<span data-ttu-id="8016c-103">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8016c-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8016c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8016c-104">Syntax</span></span>  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8016c-105">參數</span><span class="sxs-lookup"><span data-stu-id="8016c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="8016c-106">[in]若要匯出的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8016c-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="8016c-107">1.1 版的 common language runtime，匯出的型別名稱必須完全相符的名稱，`TypeDef`類型。</span><span class="sxs-lookup"><span data-stu-id="8016c-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="8016c-108">[in]語彙基元，指定匯出的型別實作的位置。</span><span class="sxs-lookup"><span data-stu-id="8016c-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="8016c-109">有效的值和其相關聯的意義如下：</span><span class="sxs-lookup"><span data-stu-id="8016c-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="8016c-110">`mdFile` 類型被實作這個組件中另一個檔案中。</span><span class="sxs-lookup"><span data-stu-id="8016c-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="8016c-111">`mdAssemblyRef` 類型被實作不同的組件中。</span><span class="sxs-lookup"><span data-stu-id="8016c-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="8016c-112">`mdExportedTYpe` 類型被巢狀其他類型。</span><span class="sxs-lookup"><span data-stu-id="8016c-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="8016c-113">`mdFileNil` 型別是在相同的檔案與資訊清單，並不是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="8016c-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="8016c-114">[in]指定要匯出類型的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8016c-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="8016c-115">在中，這個值輸入`TypeDef`實作的型別和該檔案位於這個組件時，才會相關的檔案中的資料表。</span><span class="sxs-lookup"><span data-stu-id="8016c-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="8016c-116">[in]位元組合[CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md)定義匯出的類型屬性設定的列舉值。</span><span class="sxs-lookup"><span data-stu-id="8016c-116">[in] A bitwise combination of [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="8016c-117">[out]傳回的中繼資料語彙基元，表示匯出的類型指標。</span><span class="sxs-lookup"><span data-stu-id="8016c-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8016c-118">備註</span><span class="sxs-lookup"><span data-stu-id="8016c-118">Remarks</span></span>  
 <span data-ttu-id="8016c-119">`ExportedType`必須針對每種類型，由這個組件和實作不同於包含資訊清單模組中定義中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="8016c-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8016c-120">需求</span><span class="sxs-lookup"><span data-stu-id="8016c-120">Requirements</span></span>  
 <span data-ttu-id="8016c-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8016c-121">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8016c-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8016c-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8016c-123">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8016c-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8016c-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8016c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8016c-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8016c-125">See also</span></span>

- [<span data-ttu-id="8016c-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="8016c-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
