---
title: IMetaDataImport::EnumTypeRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503740"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="8d76b-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="8d76b-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="8d76b-103">列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="8d76b-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d76b-104">語法</span><span class="sxs-lookup"><span data-stu-id="8d76b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d76b-105">參數</span><span class="sxs-lookup"><span data-stu-id="8d76b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8d76b-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="8d76b-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8d76b-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="8d76b-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="8d76b-108">脫銷用來儲存 TypeRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="8d76b-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8d76b-109">[in] `rTypeRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8d76b-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="8d76b-110">脫銷在中傳回的 TypeRef 標記數目指標 `rTypeRefs` 。</span><span class="sxs-lookup"><span data-stu-id="8d76b-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d76b-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="8d76b-111">Return Value</span></span>  
  
|<span data-ttu-id="8d76b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8d76b-112">HRESULT</span></span>|<span data-ttu-id="8d76b-113">說明</span><span class="sxs-lookup"><span data-stu-id="8d76b-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8d76b-114">`EnumTypeRefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="8d76b-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8d76b-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="8d76b-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="8d76b-116">在此情況下， `pcTypeRefs` 是零。</span><span class="sxs-lookup"><span data-stu-id="8d76b-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d76b-117">備註</span><span class="sxs-lookup"><span data-stu-id="8d76b-117">Remarks</span></span>  
 <span data-ttu-id="8d76b-118">TypeRef 標記代表類型的參考。</span><span class="sxs-lookup"><span data-stu-id="8d76b-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d76b-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="8d76b-119">Requirements</span></span>  
 <span data-ttu-id="8d76b-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d76b-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d76b-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8d76b-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d76b-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8d76b-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d76b-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d76b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d76b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d76b-124">See also</span></span>

- [<span data-ttu-id="8d76b-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8d76b-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8d76b-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8d76b-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
