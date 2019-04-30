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
ms.openlocfilehash: f15ee906fb20cb60272cee3deffa68dbe852f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042616"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="25576-102">IMetaDataImport::EnumMethodsWithName 方法</span><span class="sxs-lookup"><span data-stu-id="25576-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="25576-103">列舉具有指定名稱的方法，且該方法由指定 TypeDef 語彙基元所參考的類型定義。</span><span class="sxs-lookup"><span data-stu-id="25576-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25576-104">語法</span><span class="sxs-lookup"><span data-stu-id="25576-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="25576-105">參數</span><span class="sxs-lookup"><span data-stu-id="25576-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="25576-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="25576-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="25576-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="25576-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="25576-108">[in]TypeDef 語彙基元的方法來列舉表示的型別。</span><span class="sxs-lookup"><span data-stu-id="25576-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="25576-109">[in]列舉的範圍限制的名稱。</span><span class="sxs-lookup"><span data-stu-id="25576-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="25576-110">[out]陣列，用來儲存 methoddef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="25576-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="25576-111">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="25576-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="25576-112">[out]中傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="25576-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25576-113">備註</span><span class="sxs-lookup"><span data-stu-id="25576-113">Remarks</span></span>  
 <span data-ttu-id="25576-114">這個方法會列舉欄位和方法，但沒有屬性或事件。</span><span class="sxs-lookup"><span data-stu-id="25576-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="25576-115">不同於[imetadataimport:: Enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md)，`EnumMethodsWithName`會捨棄所有不具有指定的名稱的方法語彙基元。</span><span class="sxs-lookup"><span data-stu-id="25576-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25576-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="25576-116">Return Value</span></span>  
  
|<span data-ttu-id="25576-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25576-117">HRESULT</span></span>|<span data-ttu-id="25576-118">描述</span><span class="sxs-lookup"><span data-stu-id="25576-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="25576-119">`EnumMethodsWithName` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="25576-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="25576-120">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="25576-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="25576-121">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="25576-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25576-122">需求</span><span class="sxs-lookup"><span data-stu-id="25576-122">Requirements</span></span>  
 <span data-ttu-id="25576-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25576-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25576-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25576-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25576-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25576-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25576-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25576-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25576-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25576-127">See also</span></span>

- [<span data-ttu-id="25576-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="25576-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25576-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="25576-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
