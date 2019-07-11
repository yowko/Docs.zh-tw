---
title: IMetaDataAssemblyImport::EnumExportedTypes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62c44d0c3bd2e931b1708abb48bc9c854431419f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751145"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="56831-102">IMetaDataAssemblyImport::EnumExportedTypes 方法</span><span class="sxs-lookup"><span data-stu-id="56831-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="56831-103">列舉在目前的中繼資料範圍內的組件資訊清單中參考的匯出的類型。</span><span class="sxs-lookup"><span data-stu-id="56831-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56831-104">語法</span><span class="sxs-lookup"><span data-stu-id="56831-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56831-105">參數</span><span class="sxs-lookup"><span data-stu-id="56831-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="56831-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="56831-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="56831-107">這必須是 null 值時`EnumExportedTypes`第一次呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="56831-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="56831-108">[out]列舉`mdExportedType`中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="56831-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="56831-109">[in]最大數目`mdExportedType`語彙基元可以放入`rExportedTypes`陣列。</span><span class="sxs-lookup"><span data-stu-id="56831-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="56831-110">[out]數目`mdExportedType`語彙基元實際上置於`rExportedTypes`。</span><span class="sxs-lookup"><span data-stu-id="56831-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56831-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="56831-111">Return Value</span></span>  
  
|<span data-ttu-id="56831-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56831-112">HRESULT</span></span>|<span data-ttu-id="56831-113">說明</span><span class="sxs-lookup"><span data-stu-id="56831-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="56831-114">`EnumExportedTypes` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="56831-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="56831-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="56831-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="56831-116">在此情況下，`pcTokens`設為零。</span><span class="sxs-lookup"><span data-stu-id="56831-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56831-117">需求</span><span class="sxs-lookup"><span data-stu-id="56831-117">Requirements</span></span>  
 <span data-ttu-id="56831-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56831-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56831-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56831-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56831-120">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="56831-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56831-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56831-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56831-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56831-122">See also</span></span>

- [<span data-ttu-id="56831-123">IMetaDataAssemblyImport 介面</span><span class="sxs-lookup"><span data-stu-id="56831-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
