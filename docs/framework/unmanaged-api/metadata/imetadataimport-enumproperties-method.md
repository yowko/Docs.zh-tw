---
title: "IMetaDataImport::EnumProperties 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumProperties
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d46e18707ff6b34e32a73aed81c2b7e57f769ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumproperties-method"></a><span data-ttu-id="b1e0a-102">IMetaDataImport::EnumProperties 方法</span><span class="sxs-lookup"><span data-stu-id="b1e0a-102">IMetaDataImport::EnumProperties Method</span></span>
<span data-ttu-id="b1e0a-103">列舉 PropertyDef 語彙基元，其代表指定的 TypeDef 語彙基元所參考的類型屬性。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-103">Enumerates PropertyDef tokens representing the properties of the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1e0a-104">Syntax</span></span>  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1e0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1e0a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b1e0a-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b1e0a-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="b1e0a-108">[in]代表屬性與列舉類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-108">[in] A TypeDef token representing the type with properties to enumerate.</span></span>  
  
 `rProperties`  
 <span data-ttu-id="b1e0a-109">[out]陣列，用來儲存 PropertyDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-109">[out] The array used to store the PropertyDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b1e0a-110">[in] `rProperties` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-110">[in] The maximum size of the `rProperties` array.</span></span>  
  
 `pcProperties`  
 <span data-ttu-id="b1e0a-111">[out]PropertyDef 語彙基元中傳回的數目`rProperties`。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-111">[out] The number of PropertyDef tokens returned in `rProperties`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1e0a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1e0a-112">Return Value</span></span>  
  
|<span data-ttu-id="b1e0a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1e0a-113">HRESULT</span></span>|<span data-ttu-id="b1e0a-114">說明</span><span class="sxs-lookup"><span data-stu-id="b1e0a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b1e0a-115">`EnumProperties`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-115">`EnumProperties` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b1e0a-116">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="b1e0a-117">在此情況下，`pcProperties`為零。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-117">In that case, `pcProperties` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1e0a-118">需求</span><span class="sxs-lookup"><span data-stu-id="b1e0a-118">Requirements</span></span>  
 <span data-ttu-id="b1e0a-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1e0a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e0a-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1e0a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1e0a-121">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b1e0a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e0a-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e0a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e0a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1e0a-123">See Also</span></span>  
 [<span data-ttu-id="b1e0a-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b1e0a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b1e0a-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b1e0a-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
