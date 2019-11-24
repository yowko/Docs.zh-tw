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
ms.openlocfilehash: 1c9f15881d3515f24a63f29e9337a7a356937f2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449938"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="528d3-102">IMetaDataImport::EnumUserStrings 方法</span><span class="sxs-lookup"><span data-stu-id="528d3-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="528d3-103">列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。</span><span class="sxs-lookup"><span data-stu-id="528d3-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528d3-104">語法</span><span class="sxs-lookup"><span data-stu-id="528d3-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="528d3-105">參數</span><span class="sxs-lookup"><span data-stu-id="528d3-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="528d3-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="528d3-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="528d3-107">This must be NULL for the first call of this method.</span><span class="sxs-lookup"><span data-stu-id="528d3-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="528d3-108">[out] The array used to store the String tokens.</span><span class="sxs-lookup"><span data-stu-id="528d3-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="528d3-109">[in] `rStrings` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="528d3-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="528d3-110">[out] The number of String tokens returned in `rStrings`.</span><span class="sxs-lookup"><span data-stu-id="528d3-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="528d3-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="528d3-111">Return Value</span></span>  
  
|<span data-ttu-id="528d3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="528d3-112">HRESULT</span></span>|<span data-ttu-id="528d3-113">描述</span><span class="sxs-lookup"><span data-stu-id="528d3-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="528d3-114">`EnumUserStrings` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="528d3-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="528d3-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="528d3-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="528d3-116">In that case, `pcStrings` is zero.</span><span class="sxs-lookup"><span data-stu-id="528d3-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528d3-117">備註</span><span class="sxs-lookup"><span data-stu-id="528d3-117">Remarks</span></span>  
 <span data-ttu-id="528d3-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="528d3-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="528d3-119">This method is designed to be used by a metadata browser rather than by a compiler.</span><span class="sxs-lookup"><span data-stu-id="528d3-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="528d3-120">需求</span><span class="sxs-lookup"><span data-stu-id="528d3-120">Requirements</span></span>  
 <span data-ttu-id="528d3-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="528d3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="528d3-122">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="528d3-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="528d3-123">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="528d3-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="528d3-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="528d3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528d3-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="528d3-125">See also</span></span>

- [<span data-ttu-id="528d3-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="528d3-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="528d3-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="528d3-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
