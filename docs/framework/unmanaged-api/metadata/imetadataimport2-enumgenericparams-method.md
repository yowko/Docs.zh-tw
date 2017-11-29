---
title: "IMetaDataImport2::EnumGenericParams 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.EnumGenericParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0e6a5dc6cd1d82a3ccd46b09e301a84f90a3f429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="4c21c-102">IMetaDataImport2::EnumGenericParams 方法</span><span class="sxs-lookup"><span data-stu-id="4c21c-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="4c21c-103">陣列的泛型參數指定的 TypeDef 或 MethodDef 相關聯的語彙基元的列舉值取得語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4c21c-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c21c-104">語法</span><span class="sxs-lookup"><span data-stu-id="4c21c-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,   
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],   
   [in]  ULONG            cMax,   
   [out] ULONG            *pcGenericParams  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4c21c-105">參數</span><span class="sxs-lookup"><span data-stu-id="4c21c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4c21c-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="4c21c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="4c21c-107">[in]TypeDef 或 MethodDef 語彙基元，其泛型參數為列舉。</span><span class="sxs-lookup"><span data-stu-id="4c21c-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="4c21c-108">[out]若要列舉的泛型參數的陣列。</span><span class="sxs-lookup"><span data-stu-id="4c21c-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4c21c-109">[in]將放置在權杖的要求的數目上限`rGenericParams`。</span><span class="sxs-lookup"><span data-stu-id="4c21c-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="4c21c-110">[out]傳回的語彙基元的數字放在`rGenericParams`。</span><span class="sxs-lookup"><span data-stu-id="4c21c-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c21c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4c21c-111">Return Value</span></span>  
  
|<span data-ttu-id="4c21c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c21c-112">HRESULT</span></span>|<span data-ttu-id="4c21c-113">說明</span><span class="sxs-lookup"><span data-stu-id="4c21c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4c21c-114">`EnumGenericParams`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4c21c-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4c21c-115">`phEnum`不含任何成員的元素。</span><span class="sxs-lookup"><span data-stu-id="4c21c-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="4c21c-116">在此情況下，`pcGenericParams`設為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="4c21c-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c21c-117">需求</span><span class="sxs-lookup"><span data-stu-id="4c21c-117">Requirements</span></span>  
 <span data-ttu-id="4c21c-118">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c21c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c21c-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c21c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c21c-120">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4c21c-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c21c-121">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c21c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c21c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c21c-122">See Also</span></span>  
 [<span data-ttu-id="4c21c-123">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4c21c-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="4c21c-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4c21c-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
