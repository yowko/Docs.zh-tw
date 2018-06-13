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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8a4fe2a65244156abe1bb0da4266f949ddd3df6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447067"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="084e4-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="084e4-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="084e4-103">列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="084e4-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="084e4-104">語法</span><span class="sxs-lookup"><span data-stu-id="084e4-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="084e4-105">參數</span><span class="sxs-lookup"><span data-stu-id="084e4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="084e4-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="084e4-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="084e4-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="084e4-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="084e4-108">[out]陣列，用來儲存 typeref 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="084e4-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="084e4-109">[in] `rTypeRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="084e4-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="084e4-110">[out]傳回的 typeref 語彙基元數目的指標`rTypeRefs`。</span><span class="sxs-lookup"><span data-stu-id="084e4-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="084e4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="084e4-111">Return Value</span></span>  
  
|<span data-ttu-id="084e4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="084e4-112">HRESULT</span></span>|<span data-ttu-id="084e4-113">描述</span><span class="sxs-lookup"><span data-stu-id="084e4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="084e4-114">`EnumTypeRefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="084e4-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="084e4-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="084e4-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="084e4-116">在此情況下，`pcTypeRefs`為零。</span><span class="sxs-lookup"><span data-stu-id="084e4-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="084e4-117">備註</span><span class="sxs-lookup"><span data-stu-id="084e4-117">Remarks</span></span>  
 <span data-ttu-id="084e4-118">TypeRef 語彙基元代表類型的參考。</span><span class="sxs-lookup"><span data-stu-id="084e4-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="084e4-119">需求</span><span class="sxs-lookup"><span data-stu-id="084e4-119">Requirements</span></span>  
 <span data-ttu-id="084e4-120">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="084e4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="084e4-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="084e4-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="084e4-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="084e4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="084e4-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="084e4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="084e4-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="084e4-124">See Also</span></span>  
 [<span data-ttu-id="084e4-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="084e4-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="084e4-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="084e4-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
