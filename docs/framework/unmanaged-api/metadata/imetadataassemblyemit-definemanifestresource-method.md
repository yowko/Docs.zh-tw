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
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432061"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="2169a-102">IMetaDataAssemblyEmit::DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="2169a-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="2169a-103">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2169a-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2169a-104">語法</span><span class="sxs-lookup"><span data-stu-id="2169a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2169a-105">參數</span><span class="sxs-lookup"><span data-stu-id="2169a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="2169a-106">在資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="2169a-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="2169a-107">在對應至資源提供者 `mdtFile` 或 `mdtAssemblyRef` 類型的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="2169a-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="2169a-108">Null 值表示內嵌中繼資料的檔案是資源提供者。</span><span class="sxs-lookup"><span data-stu-id="2169a-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="2169a-109">在檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="2169a-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="2169a-110">對於獨立檔案中的資源，這一律會是零。</span><span class="sxs-lookup"><span data-stu-id="2169a-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="2169a-111">如果資源內嵌在 PE （可移植的可執行檔）檔案中，這就是資源 BLOB 的位移，它會從 cor 標頭檔中指定的位置開始。</span><span class="sxs-lookup"><span data-stu-id="2169a-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="2169a-112">在旗標值的位元組合，這個組合會指定資源定義的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="2169a-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="2169a-113">脫銷傳回之元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="2169a-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2169a-114">備註</span><span class="sxs-lookup"><span data-stu-id="2169a-114">Remarks</span></span>  
 <span data-ttu-id="2169a-115">您必須針對每個元件檔案中所實作為的每個資源，定義一個 `ManifestResource` 元資料結構。</span><span class="sxs-lookup"><span data-stu-id="2169a-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2169a-116">需求</span><span class="sxs-lookup"><span data-stu-id="2169a-116">Requirements</span></span>  
 <span data-ttu-id="2169a-117">**平臺：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2169a-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2169a-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2169a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2169a-119">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="2169a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2169a-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2169a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2169a-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="2169a-121">See also</span></span>

- [<span data-ttu-id="2169a-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="2169a-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
