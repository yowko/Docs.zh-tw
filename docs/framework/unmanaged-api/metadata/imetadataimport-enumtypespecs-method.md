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
ms.openlocfilehash: 94b4c3935c949c0c4008e41244713b6bfa4dba84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503714"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="6bb48-102">IMetaDataImport::EnumTypeSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="6bb48-102">IMetaDataImport::EnumTypeSpecs Method</span></span>
<span data-ttu-id="6bb48-103">列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6bb48-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb48-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bb48-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bb48-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bb48-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6bb48-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="6bb48-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="6bb48-107">這個方法的第一次呼叫時，這個值必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="6bb48-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="6bb48-108">脫銷用來儲存 TypeSpec 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="6bb48-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6bb48-109">[in] `rTypeSpecs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6bb48-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="6bb48-110">脫銷在中傳回的 TypeSpec token 數目 `rTypeSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="6bb48-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bb48-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6bb48-111">Return Value</span></span>  
  
|<span data-ttu-id="6bb48-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bb48-112">HRESULT</span></span>|<span data-ttu-id="6bb48-113">說明</span><span class="sxs-lookup"><span data-stu-id="6bb48-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6bb48-114">`EnumTypeSpecs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="6bb48-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6bb48-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="6bb48-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="6bb48-116">在此情況下， `pcTypeSpecs` 是零。</span><span class="sxs-lookup"><span data-stu-id="6bb48-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bb48-117">備註</span><span class="sxs-lookup"><span data-stu-id="6bb48-117">Remarks</span></span>  
 <span data-ttu-id="6bb48-118">TypeSpec 標記是由[IMetaDataEmit：： GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="6bb48-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb48-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="6bb48-119">Requirements</span></span>  
 <span data-ttu-id="6bb48-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bb48-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb48-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6bb48-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bb48-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6bb48-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bb48-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb48-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb48-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bb48-124">See also</span></span>

- [<span data-ttu-id="6bb48-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6bb48-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6bb48-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6bb48-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
