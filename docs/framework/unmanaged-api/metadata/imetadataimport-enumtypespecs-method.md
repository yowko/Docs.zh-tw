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
ms.openlocfilehash: 38c9f8df12b0fc83a236d2cb7c32d1198be7096d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719810"
---
# <a name="imetadataimportenumtypespecs-method"></a><span data-ttu-id="c3f94-102">IMetaDataImport::EnumTypeSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="c3f94-102">IMetaDataImport::EnumTypeSpecs Method</span></span>

<span data-ttu-id="c3f94-103">列舉在目前中繼資料範圍中定義的 TypeSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="c3f94-103">Enumerates TypeSpec tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f94-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3f94-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f94-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3f94-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c3f94-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="c3f94-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c3f94-107">第一次呼叫這個方法時，這個值必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="c3f94-107">This value must be NULL for the first call of this method.</span></span>  
  
 `rTypeSpecs`  
 <span data-ttu-id="c3f94-108">擴展用來儲存 TypeSpec 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="c3f94-108">[out] The array used to store the TypeSpec tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c3f94-109">[in] `rTypeSpecs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="c3f94-109">[in] The maximum size of the `rTypeSpecs` array.</span></span>  
  
 `pcTypeSpecs`  
 <span data-ttu-id="c3f94-110">擴展中傳回的 TypeSpec 權杖數目 `rTypeSpecs` 。</span><span class="sxs-lookup"><span data-stu-id="c3f94-110">[out] The number of TypeSpec tokens returned in `rTypeSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3f94-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3f94-111">Return Value</span></span>  
  
|<span data-ttu-id="c3f94-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c3f94-112">HRESULT</span></span>|<span data-ttu-id="c3f94-113">描述</span><span class="sxs-lookup"><span data-stu-id="c3f94-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c3f94-114">`EnumTypeSpecs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="c3f94-114">`EnumTypeSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c3f94-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="c3f94-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c3f94-116">在此情況下， `pcTypeSpecs` 是零。</span><span class="sxs-lookup"><span data-stu-id="c3f94-116">In that case, `pcTypeSpecs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3f94-117">備註</span><span class="sxs-lookup"><span data-stu-id="c3f94-117">Remarks</span></span>  

 <span data-ttu-id="c3f94-118">TypeSpec 標記是由 [IMetaDataEmit：： GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) 方法所建立。</span><span class="sxs-lookup"><span data-stu-id="c3f94-118">The TypeSpec tokens are created by the [IMetaDataEmit::GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f94-119">需求</span><span class="sxs-lookup"><span data-stu-id="c3f94-119">Requirements</span></span>  

 <span data-ttu-id="c3f94-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3f94-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f94-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c3f94-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3f94-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c3f94-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3f94-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f94-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f94-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3f94-124">See also</span></span>

- [<span data-ttu-id="c3f94-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c3f94-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c3f94-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c3f94-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
