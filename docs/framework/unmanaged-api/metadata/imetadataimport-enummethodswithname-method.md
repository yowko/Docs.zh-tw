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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5de55d74741e9deb33be2f9adf15a970561664b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779727"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="dc4cb-102">IMetaDataImport::EnumMethodsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="dc4cb-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="dc4cb-103">列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4cb-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc4cb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc4cb-105">參數</span><span class="sxs-lookup"><span data-stu-id="dc4cb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="dc4cb-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dc4cb-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="dc4cb-108">[in]TypeDef 語彙基元的方法來列舉表示的型別。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="dc4cb-109">[in]列舉的範圍限制的名稱。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="dc4cb-110">[out]陣列，用來儲存 methoddef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dc4cb-111">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dc4cb-112">[out]中傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc4cb-113">備註</span><span class="sxs-lookup"><span data-stu-id="dc4cb-113">Remarks</span></span>  
 <span data-ttu-id="dc4cb-114">這個方法會列舉欄位和方法，但沒有屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="dc4cb-115">不同於[imetadataimport:: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)，`EnumMethodsWithName`會捨棄所有不具有指定的名稱的方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc4cb-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="dc4cb-116">Return Value</span></span>  
  
|<span data-ttu-id="dc4cb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc4cb-117">HRESULT</span></span>|<span data-ttu-id="dc4cb-118">說明</span><span class="sxs-lookup"><span data-stu-id="dc4cb-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dc4cb-119">`EnumMethodsWithName` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dc4cb-120">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="dc4cb-121">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc4cb-122">需求</span><span class="sxs-lookup"><span data-stu-id="dc4cb-122">Requirements</span></span>  
 <span data-ttu-id="dc4cb-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dc4cb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc4cb-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc4cb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc4cb-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="dc4cb-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc4cb-126">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc4cb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc4cb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc4cb-127">See also</span></span>

- [<span data-ttu-id="dc4cb-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="dc4cb-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dc4cb-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="dc4cb-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
