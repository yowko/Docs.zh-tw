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
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449977"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="6fb72-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="6fb72-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="6fb72-103">列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6fb72-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fb72-104">語法</span><span class="sxs-lookup"><span data-stu-id="6fb72-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fb72-105">參數</span><span class="sxs-lookup"><span data-stu-id="6fb72-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6fb72-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="6fb72-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6fb72-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="6fb72-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="6fb72-108">脫銷用來儲存 TypeRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="6fb72-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6fb72-109">[in] `rTypeRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6fb72-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="6fb72-110">脫銷`rTypeRefs`中傳回之 TypeRef token 數目的指標。</span><span class="sxs-lookup"><span data-stu-id="6fb72-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fb72-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6fb72-111">Return Value</span></span>  
  
|<span data-ttu-id="6fb72-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6fb72-112">HRESULT</span></span>|<span data-ttu-id="6fb72-113">描述</span><span class="sxs-lookup"><span data-stu-id="6fb72-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6fb72-114">已成功傳回 `EnumTypeRefs`。</span><span class="sxs-lookup"><span data-stu-id="6fb72-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6fb72-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="6fb72-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6fb72-116">在此情況下，`pcTypeRefs` 為零。</span><span class="sxs-lookup"><span data-stu-id="6fb72-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fb72-117">備註</span><span class="sxs-lookup"><span data-stu-id="6fb72-117">Remarks</span></span>  
 <span data-ttu-id="6fb72-118">TypeRef 標記代表類型的參考。</span><span class="sxs-lookup"><span data-stu-id="6fb72-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fb72-119">需求</span><span class="sxs-lookup"><span data-stu-id="6fb72-119">Requirements</span></span>  
 <span data-ttu-id="6fb72-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6fb72-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fb72-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6fb72-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6fb72-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6fb72-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6fb72-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fb72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb72-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6fb72-124">See also</span></span>

- [<span data-ttu-id="6fb72-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6fb72-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6fb72-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6fb72-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
