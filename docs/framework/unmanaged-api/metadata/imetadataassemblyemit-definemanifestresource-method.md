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
ms.openlocfilehash: 3729f06097fa4dce6de009307183d5e97c24479b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728299"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="3b499-102">IMetaDataAssemblyEmit::DefineManifestResource 方法</span><span class="sxs-lookup"><span data-stu-id="3b499-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>

<span data-ttu-id="3b499-103">為指定的資訊清單資源，建立包含其中繼資料的 `ManifestResource` 結構，並且傳回關聯的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3b499-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b499-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b499-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,
    [in] mdToken                tkImplementation,
    [in] DWORD                  dwOffset,
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b499-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b499-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="3b499-106">在資源的名稱。</span><span class="sxs-lookup"><span data-stu-id="3b499-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="3b499-107">在 `mdtFile` 或 `mdtAssemblyRef` 對應至資源提供者之類型的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="3b499-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="3b499-108">Null 值表示內嵌中繼資料的檔案是資源提供者。</span><span class="sxs-lookup"><span data-stu-id="3b499-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="3b499-109">在檔案內資源開頭的位移。</span><span class="sxs-lookup"><span data-stu-id="3b499-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="3b499-110">針對獨立檔案中的資源，這一律會是零。</span><span class="sxs-lookup"><span data-stu-id="3b499-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="3b499-111">如果資源內嵌于 PE (可攜式可執行檔) 檔案中，這就是資源 BLOB 的位移，它會從 cor .h 標頭檔中指定的位置開始。</span><span class="sxs-lookup"><span data-stu-id="3b499-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="3b499-112">在旗標值的位元組合，這些值會指定資源定義的屬性設定。</span><span class="sxs-lookup"><span data-stu-id="3b499-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="3b499-113">擴展傳回之元資料標記的指標。</span><span class="sxs-lookup"><span data-stu-id="3b499-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b499-114">備註</span><span class="sxs-lookup"><span data-stu-id="3b499-114">Remarks</span></span>  

 <span data-ttu-id="3b499-115">您 `ManifestResource` 必須為每個元件檔案中所執行的每個資源定義一個元資料結構。</span><span class="sxs-lookup"><span data-stu-id="3b499-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b499-116">需求</span><span class="sxs-lookup"><span data-stu-id="3b499-116">Requirements</span></span>  

 <span data-ttu-id="3b499-117">**平臺：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b499-117">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b499-118">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3b499-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b499-119">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3b499-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b499-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b499-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b499-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b499-121">See also</span></span>

- [<span data-ttu-id="3b499-122">IMetaDataAssemblyEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3b499-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
