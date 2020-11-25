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
ms.openlocfilehash: 5b5345fc4819716dc6c2a00323f94546cfc67f32
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720928"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="64ec9-102">IMetaDataImport::EnumMethodsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="64ec9-102">IMetaDataImport::EnumMethodsWithName Method</span></span>

<span data-ttu-id="64ec9-103">列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。</span><span class="sxs-lookup"><span data-stu-id="64ec9-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ec9-104">語法</span><span class="sxs-lookup"><span data-stu-id="64ec9-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="64ec9-105">參數</span><span class="sxs-lookup"><span data-stu-id="64ec9-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="64ec9-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="64ec9-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="64ec9-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="64ec9-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="64ec9-108">在表示要列舉其方法之類型的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="64ec9-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="64ec9-109">在限制列舉範圍的名稱。</span><span class="sxs-lookup"><span data-stu-id="64ec9-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="64ec9-110">擴展用來儲存 MethodDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="64ec9-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="64ec9-111">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="64ec9-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="64ec9-112">擴展中傳回的 MethodDef 權杖數目 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="64ec9-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64ec9-113">備註</span><span class="sxs-lookup"><span data-stu-id="64ec9-113">Remarks</span></span>  

 <span data-ttu-id="64ec9-114">這個方法會列舉欄位和方法，但不會列舉屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="64ec9-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="64ec9-115">不同于 [IMetaDataImport：： EnumMethods](imetadataimport-enummethods-method.md)，會 `EnumMethodsWithName` 捨棄所有沒有指定名稱的方法標記。</span><span class="sxs-lookup"><span data-stu-id="64ec9-115">Unlike [IMetaDataImport::EnumMethods](imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64ec9-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="64ec9-116">Return Value</span></span>  
  
|<span data-ttu-id="64ec9-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64ec9-117">HRESULT</span></span>|<span data-ttu-id="64ec9-118">描述</span><span class="sxs-lookup"><span data-stu-id="64ec9-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="64ec9-119">`EnumMethodsWithName` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="64ec9-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="64ec9-120">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="64ec9-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="64ec9-121">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="64ec9-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="64ec9-122">需求</span><span class="sxs-lookup"><span data-stu-id="64ec9-122">Requirements</span></span>  

 <span data-ttu-id="64ec9-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64ec9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64ec9-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="64ec9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64ec9-125">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="64ec9-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="64ec9-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64ec9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ec9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64ec9-127">See also</span></span>

- [<span data-ttu-id="64ec9-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="64ec9-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="64ec9-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="64ec9-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
