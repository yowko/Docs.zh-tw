---
title: IMetaDataAssemblyEmit::DefineManifestResource 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 5aa5d78faa8ca9261594e2a649b11088e1d78ee7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177862"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="b3c0c-102">IMetaDataAssemblyEmit::DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="b3c0c-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="b3c0c-103">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c0c-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3c0c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3c0c-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3c0c-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b3c0c-106">[在]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="b3c0c-107">[在]類型的`mdtFile`中繼資料權杖或`mdtAssemblyRef`映射到資來源提供者的中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="b3c0c-108">Null 值表示嵌入中繼資料的檔是資來源提供者。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="b3c0c-109">[在]檔中資源開頭的偏移量。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="b3c0c-110">對於獨立檔中的資源，這始終為零。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="b3c0c-111">如果資源嵌入到 PE（可攜式可執行檔）檔中，這是資源 BLOB 的偏移量，它從 cor.h 標標頭檔中指定的位置開始。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="b3c0c-112">[在]指定資源定義的屬性設置的標誌值的位組合。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="b3c0c-113">[出]指向返回的中繼資料權杖的指標。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3c0c-114">備註</span><span class="sxs-lookup"><span data-stu-id="b3c0c-114">Remarks</span></span>  
 <span data-ttu-id="b3c0c-115">必須`ManifestResource`為每個程式集檔中實現的每個資源定義一個元資料結構。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c0c-116">需求</span><span class="sxs-lookup"><span data-stu-id="b3c0c-116">Requirements</span></span>  
 <span data-ttu-id="b3c0c-117">**平臺：** 請參閱[系統要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3c0c-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c0c-118">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b3c0c-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3c0c-119">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3c0c-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3c0c-120">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c0c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c0c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3c0c-121">See also</span></span>

- [<span data-ttu-id="b3c0c-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b3c0c-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
