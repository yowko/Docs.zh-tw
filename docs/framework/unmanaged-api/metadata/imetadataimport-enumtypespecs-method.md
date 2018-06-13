---
title: IMetaDataImport::EnumTypeSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9b9bc8e364342a601c0738d5a64c5eac3cb7e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447706"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="c0c3d-102">IMetaDataImport::EnumTypeSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="c0c3d-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="c0c3d-103">列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0c3d-104">Syntax</span></span>  
  
```  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0c3d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0c3d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c0c3d-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c0c3d-107">此值必須是 NULL，這個方法的第一個呼叫。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="c0c3d-108">[out]陣列，用來儲存的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c0c3d-109">[in] `rTypeSpecs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="c0c3d-110">[out]傳回的 TypeSpec 語彙基元數目`rTypeSpecs`。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0c3d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c0c3d-111">Return Value</span></span>  
  
|<span data-ttu-id="c0c3d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0c3d-112">HRESULT</span></span>|<span data-ttu-id="c0c3d-113">描述</span><span class="sxs-lookup"><span data-stu-id="c0c3d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c0c3d-114">`EnumTypeSpecs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c0c3d-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c0c3d-116">在此情況下，`pcTypeSpecs`為零。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0c3d-117">備註</span><span class="sxs-lookup"><span data-stu-id="c0c3d-117">Remarks</span></span>  
 <span data-ttu-id="c0c3d-118">所建立的 TypeSpec 語彙基元[imetadataemit:: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0c3d-119">需求</span><span class="sxs-lookup"><span data-stu-id="c0c3d-119">Requirements</span></span>  
 <span data-ttu-id="c0c3d-120">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0c3d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c3d-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0c3d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0c3d-122">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c0c3d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0c3d-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0c3d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c3d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0c3d-124">See Also</span></span>  
 [<span data-ttu-id="c0c3d-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c0c3d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c0c3d-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c0c3d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
