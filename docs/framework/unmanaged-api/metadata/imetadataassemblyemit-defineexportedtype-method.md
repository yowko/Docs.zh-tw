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
ms.openlocfilehash: 6b30218cc7373494870ec54a3196857fcc5c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689390"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="3d95f-102">IMetaDataAssemblyEmit::DefineExportedType 方法</span><span class="sxs-lookup"><span data-stu-id="3d95f-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="3d95f-103">為指定的已匯出類型，建立包含其中繼資料的 `ExportedType` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3d95f-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d95f-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d95f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d95f-105">參數</span><span class="sxs-lookup"><span data-stu-id="3d95f-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="3d95f-106">在要匯出之類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3d95f-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="3d95f-107">若為 common language runtime 的1.1 版，則匯出的類型名稱必須完全符合中為類型指定的名稱 `TypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="3d95f-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="3d95f-108">在指定所匯出型別執行位置的標記。</span><span class="sxs-lookup"><span data-stu-id="3d95f-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="3d95f-109">有效值及其相關聯的意義如下：</span><span class="sxs-lookup"><span data-stu-id="3d95f-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="3d95f-110">`mdFile` 此類型會在此元件內的不同檔案中執行。</span><span class="sxs-lookup"><span data-stu-id="3d95f-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="3d95f-111">`mdAssemblyRef` 此類型會在不同的元件中執行。</span><span class="sxs-lookup"><span data-stu-id="3d95f-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="3d95f-112">`mdExportedTYpe` 類型會在其他類型中嵌套。</span><span class="sxs-lookup"><span data-stu-id="3d95f-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="3d95f-113">`mdFileNil` 此類型與資訊清單位於相同的檔案中，而不是巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="3d95f-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="3d95f-114">在中繼資料的標記，這個中繼資料會指定要匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="3d95f-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="3d95f-115">此值會在執行類型的檔案中的 `TypeDef` 資料表中輸入，而且只有在該檔案位於此元件中時才會相關。</span><span class="sxs-lookup"><span data-stu-id="3d95f-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="3d95f-116">在 [CorTypeAttr](cortypeattr-enumeration.md) 列舉值的位元組合，這些值會定義匯出型別的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="3d95f-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="3d95f-117">擴展傳回之元資料標記的指標，指出匯出的型別。</span><span class="sxs-lookup"><span data-stu-id="3d95f-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d95f-118">備註</span><span class="sxs-lookup"><span data-stu-id="3d95f-118">Remarks</span></span>  

 <span data-ttu-id="3d95f-119">您 `ExportedType` 必須為這個元件所公開的每個型別定義元資料結構，並且在包含資訊清單的模組以外的模組中執行。</span><span class="sxs-lookup"><span data-stu-id="3d95f-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d95f-120">需求</span><span class="sxs-lookup"><span data-stu-id="3d95f-120">Requirements</span></span>  

 <span data-ttu-id="3d95f-121">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d95f-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d95f-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3d95f-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d95f-123">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3d95f-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d95f-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d95f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d95f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d95f-125">See also</span></span>

- [<span data-ttu-id="3d95f-126">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3d95f-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
