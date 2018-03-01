---
title: "IMetaDataImport::EnumMethodsWithName 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9f16e66f83925104c4be1e69a476e398f33295a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="751de-102">IMetaDataImport::EnumMethodsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="751de-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="751de-103">列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。</span><span class="sxs-lookup"><span data-stu-id="751de-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="751de-104">語法</span><span class="sxs-lookup"><span data-stu-id="751de-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="751de-105">參數</span><span class="sxs-lookup"><span data-stu-id="751de-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="751de-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="751de-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="751de-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="751de-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="751de-108">[in]代表其方法來列舉類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="751de-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="751de-109">[in]列舉的範圍限制的名稱。</span><span class="sxs-lookup"><span data-stu-id="751de-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="751de-110">[out]陣列，用來儲存 methoddef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="751de-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="751de-111">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="751de-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="751de-112">[out]傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="751de-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="751de-113">備註</span><span class="sxs-lookup"><span data-stu-id="751de-113">Remarks</span></span>  
 <span data-ttu-id="751de-114">這個方法會列舉欄位和方法，但沒有屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="751de-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="751de-115">不同於[imetadataimport:: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)，`EnumMethodsWithName`捨棄不具有指定的名稱的所有方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="751de-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="751de-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="751de-116">Return Value</span></span>  
  
|<span data-ttu-id="751de-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="751de-117">HRESULT</span></span>|<span data-ttu-id="751de-118">描述</span><span class="sxs-lookup"><span data-stu-id="751de-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="751de-119">`EnumMethodsWithName`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="751de-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="751de-120">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="751de-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="751de-121">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="751de-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="751de-122">需求</span><span class="sxs-lookup"><span data-stu-id="751de-122">Requirements</span></span>  
 <span data-ttu-id="751de-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="751de-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="751de-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="751de-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="751de-125">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="751de-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="751de-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="751de-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751de-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="751de-127">See Also</span></span>  
 [<span data-ttu-id="751de-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="751de-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="751de-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="751de-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
