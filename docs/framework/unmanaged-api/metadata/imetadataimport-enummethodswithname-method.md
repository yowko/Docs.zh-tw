---
title: IMetaDataImport::EnumMethodsWithName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
ms.openlocfilehash: 66a09baea1df2e2de418bdce8821672802f1f51f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491728"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="22cd1-102">IMetaDataImport::EnumMethodsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="22cd1-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="22cd1-103">列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。</span><span class="sxs-lookup"><span data-stu-id="22cd1-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22cd1-104">語法</span><span class="sxs-lookup"><span data-stu-id="22cd1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22cd1-105">參數</span><span class="sxs-lookup"><span data-stu-id="22cd1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="22cd1-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="22cd1-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="22cd1-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="22cd1-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="22cd1-108">在TypeDef token，代表要列舉其方法的類型。</span><span class="sxs-lookup"><span data-stu-id="22cd1-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="22cd1-109">在限制列舉範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="22cd1-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="22cd1-110">脫銷用來儲存 MethodDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="22cd1-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="22cd1-111">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="22cd1-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="22cd1-112">脫銷在中傳回的 MethodDef 標記數目 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="22cd1-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22cd1-113">備註</span><span class="sxs-lookup"><span data-stu-id="22cd1-113">Remarks</span></span>  
 <span data-ttu-id="22cd1-114">這個方法會列舉欄位和方法，而不是屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="22cd1-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="22cd1-115">不同于[IMetaDataImport：： EnumMethods](imetadataimport-enummethods-method.md)，會 `EnumMethodsWithName` 捨棄所有沒有指定名稱的方法標記。</span><span class="sxs-lookup"><span data-stu-id="22cd1-115">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22cd1-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="22cd1-116">Return Value</span></span>  
  
|<span data-ttu-id="22cd1-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22cd1-117">HRESULT</span></span>|<span data-ttu-id="22cd1-118">說明</span><span class="sxs-lookup"><span data-stu-id="22cd1-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="22cd1-119">`EnumMethodsWithName`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="22cd1-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="22cd1-120">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="22cd1-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="22cd1-121">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="22cd1-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22cd1-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="22cd1-122">Requirements</span></span>  
 <span data-ttu-id="22cd1-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22cd1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22cd1-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="22cd1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22cd1-125">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="22cd1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22cd1-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22cd1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22cd1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22cd1-127">See also</span></span>

- [<span data-ttu-id="22cd1-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="22cd1-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="22cd1-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="22cd1-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
