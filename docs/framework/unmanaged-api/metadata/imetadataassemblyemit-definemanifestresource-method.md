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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 145659e8761b8c7804faf25e47a280a9d4f874b4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679028"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="abdd3-102">IMetaDataAssemblyEmit::DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="abdd3-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="abdd3-103">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="abdd3-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="abdd3-104">Syntax</span></span>  
  
```  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abdd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="abdd3-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="abdd3-106">[in]資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="abdd3-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="abdd3-107">[in]型別的中繼資料語彙基元`mdtFile`或`mdtAssemblyRef`子可對應到資源提供者。</span><span class="sxs-lookup"><span data-stu-id="abdd3-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="abdd3-108">NULL 值表示在其中內嵌中繼資料檔案是資源提供者。</span><span class="sxs-lookup"><span data-stu-id="abdd3-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="abdd3-109">[in]資源檔中的開始位移。</span><span class="sxs-lookup"><span data-stu-id="abdd3-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="abdd3-110">如需獨立檔案中的資源，這一律為零。</span><span class="sxs-lookup"><span data-stu-id="abdd3-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="abdd3-111">如果資源內嵌 PE （可攜式執行檔） 中，這會是資源的 BLOB，cor.h 標頭檔中指定的位置開始的位移。</span><span class="sxs-lookup"><span data-stu-id="abdd3-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="abdd3-112">[in]指定資源定義的屬性設定的旗標值的位元組合。</span><span class="sxs-lookup"><span data-stu-id="abdd3-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="abdd3-113">[out]傳回的中繼資料語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="abdd3-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abdd3-114">備註</span><span class="sxs-lookup"><span data-stu-id="abdd3-114">Remarks</span></span>  
 <span data-ttu-id="abdd3-115">一個`ManifestResource`必須定義在每個組件的檔案中實作每個資源的中繼資料結構。</span><span class="sxs-lookup"><span data-stu-id="abdd3-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abdd3-116">需求</span><span class="sxs-lookup"><span data-stu-id="abdd3-116">Requirements</span></span>  
 <span data-ttu-id="abdd3-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abdd3-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abdd3-118">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abdd3-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abdd3-119">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="abdd3-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abdd3-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abdd3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdd3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abdd3-121">See also</span></span>
- [<span data-ttu-id="abdd3-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="abdd3-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
