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
ms.openlocfilehash: e5d4ddd43b27d733a63c2e0dc5e92ffd2ba94a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175430"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="0ff33-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="0ff33-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="0ff33-103">列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0ff33-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff33-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ff33-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ff33-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ff33-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="0ff33-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="0ff33-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="0ff33-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="0ff33-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="0ff33-108">[出]用於存儲 TypeRef 權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="0ff33-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0ff33-109">[in] `rTypeRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="0ff33-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="0ff33-110">[出]指向 在 中`rTypeRefs`返回的 TypeRef 權杖數的指標。</span><span class="sxs-lookup"><span data-stu-id="0ff33-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ff33-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ff33-111">Return Value</span></span>  
  
|<span data-ttu-id="0ff33-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ff33-112">HRESULT</span></span>|<span data-ttu-id="0ff33-113">描述</span><span class="sxs-lookup"><span data-stu-id="0ff33-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0ff33-114">`EnumTypeRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="0ff33-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0ff33-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="0ff33-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="0ff33-116">在這種情況下，`pcTypeRefs`為零。</span><span class="sxs-lookup"><span data-stu-id="0ff33-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ff33-117">備註</span><span class="sxs-lookup"><span data-stu-id="0ff33-117">Remarks</span></span>  
 <span data-ttu-id="0ff33-118">TypeRef 權杖表示對類型的引用。</span><span class="sxs-lookup"><span data-stu-id="0ff33-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ff33-119">需求</span><span class="sxs-lookup"><span data-stu-id="0ff33-119">Requirements</span></span>  
 <span data-ttu-id="0ff33-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ff33-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ff33-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="0ff33-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ff33-122">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="0ff33-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ff33-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ff33-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff33-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ff33-124">See also</span></span>

- [<span data-ttu-id="0ff33-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="0ff33-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0ff33-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="0ff33-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
