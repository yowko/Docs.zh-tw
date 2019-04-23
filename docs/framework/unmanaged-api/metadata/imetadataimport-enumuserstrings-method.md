---
title: IMetaDataImport::EnumUserStrings 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4be12e46851b11a5e6db60c351094a356fa61f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082941"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="abb54-102">IMetaDataImport::EnumUserStrings 方法</span><span class="sxs-lookup"><span data-stu-id="abb54-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="abb54-103">列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。</span><span class="sxs-lookup"><span data-stu-id="abb54-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb54-104">語法</span><span class="sxs-lookup"><span data-stu-id="abb54-104">Syntax</span></span>  
  
```  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abb54-105">參數</span><span class="sxs-lookup"><span data-stu-id="abb54-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="abb54-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="abb54-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="abb54-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="abb54-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="abb54-108">[out]陣列，用來儲存的字串語彙基元。</span><span class="sxs-lookup"><span data-stu-id="abb54-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="abb54-109">[in] `rStrings` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="abb54-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="abb54-110">[out]中傳回的字串語彙基元數目`rStrings`。</span><span class="sxs-lookup"><span data-stu-id="abb54-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abb54-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="abb54-111">Return Value</span></span>  
  
|<span data-ttu-id="abb54-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abb54-112">HRESULT</span></span>|<span data-ttu-id="abb54-113">描述</span><span class="sxs-lookup"><span data-stu-id="abb54-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="abb54-114">`EnumUserStrings` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="abb54-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="abb54-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="abb54-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="abb54-116">在此情況下，`pcStrings`為零。</span><span class="sxs-lookup"><span data-stu-id="abb54-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb54-117">備註</span><span class="sxs-lookup"><span data-stu-id="abb54-117">Remarks</span></span>  
 <span data-ttu-id="abb54-118">所建立的字串語彙基元[imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="abb54-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="abb54-119">這個方法被設計來由中繼資料瀏覽器中，而不是由編譯器。</span><span class="sxs-lookup"><span data-stu-id="abb54-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb54-120">需求</span><span class="sxs-lookup"><span data-stu-id="abb54-120">Requirements</span></span>  
 <span data-ttu-id="abb54-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abb54-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb54-122">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abb54-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abb54-123">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="abb54-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abb54-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb54-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb54-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abb54-125">See also</span></span>

- [<span data-ttu-id="abb54-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="abb54-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="abb54-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="abb54-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
