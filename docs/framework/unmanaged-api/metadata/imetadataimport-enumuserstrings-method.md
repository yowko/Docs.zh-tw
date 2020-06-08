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
ms.openlocfilehash: cd164008098c053e7d6506a6eef7d3bc8e4274b6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503693"
---
# <a name="imetadataimportenumuserstrings-method"></a><span data-ttu-id="c4ec7-102">IMetaDataImport::EnumUserStrings 方法</span><span class="sxs-lookup"><span data-stu-id="c4ec7-102">IMetaDataImport::EnumUserStrings Method</span></span>
<span data-ttu-id="c4ec7-103">列舉字串語彙基元，其代表目前中繼資料範圍內的硬式編碼字串。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-103">Enumerates String tokens representing hard-coded strings in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ec7-104">語法</span><span class="sxs-lookup"><span data-stu-id="c4ec7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ec7-105">參數</span><span class="sxs-lookup"><span data-stu-id="c4ec7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c4ec7-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c4ec7-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-107">This must be NULL for the first call of this method.</span></span>  
  
 `rStrings`  
 <span data-ttu-id="c4ec7-108">脫銷用來儲存字串標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-108">[out] The array used to store the String tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c4ec7-109">[in] `rStrings` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-109">[in] The maximum size of the `rStrings` array.</span></span>  
  
 `pcStrings`  
 <span data-ttu-id="c4ec7-110">脫銷在中傳回的字串標記數目 `rStrings` 。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-110">[out] The number of String tokens returned in `rStrings`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4ec7-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c4ec7-111">Return Value</span></span>  
  
|<span data-ttu-id="c4ec7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4ec7-112">HRESULT</span></span>|<span data-ttu-id="c4ec7-113">說明</span><span class="sxs-lookup"><span data-stu-id="c4ec7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c4ec7-114">`EnumUserStrings`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-114">`EnumUserStrings` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c4ec7-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c4ec7-116">在此情況下， `pcStrings` 是零。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-116">In that case, `pcStrings` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4ec7-117">備註</span><span class="sxs-lookup"><span data-stu-id="c4ec7-117">Remarks</span></span>  
 <span data-ttu-id="c4ec7-118">字串標記是由[IMetaDataEmit：:D efineuserstring](imetadataemit-defineuserstring-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-118">The String tokens are created by the [IMetaDataEmit::DefineUserString](imetadataemit-defineuserstring-method.md) method.</span></span> <span data-ttu-id="c4ec7-119">這個方法是設計用來供中繼資料瀏覽器使用，而不是編譯器。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-119">This method is designed to be used by a metadata browser rather than by a compiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ec7-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="c4ec7-120">Requirements</span></span>  
 <span data-ttu-id="c4ec7-121">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c4ec7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ec7-122">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c4ec7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4ec7-123">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c4ec7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4ec7-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ec7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ec7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4ec7-125">See also</span></span>

- [<span data-ttu-id="c4ec7-126">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c4ec7-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c4ec7-127">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c4ec7-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
