---
title: "IMetaDataImport::EnumParams 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumParams
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51544a44ed4bae25d4214e25c717769a8446f0f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="45e23-102">IMetaDataImport::EnumParams 方法</span><span class="sxs-lookup"><span data-stu-id="45e23-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="45e23-103">列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="45e23-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e23-104">語法</span><span class="sxs-lookup"><span data-stu-id="45e23-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45e23-105">參數</span><span class="sxs-lookup"><span data-stu-id="45e23-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="45e23-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="45e23-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="45e23-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="45e23-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="45e23-108">[in]代表列舉參數的方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="45e23-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="45e23-109">[out]陣列，用來儲存 ParamDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="45e23-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="45e23-110">[in] `rParams` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="45e23-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="45e23-111">[out]ParamDef 語彙基元中傳回的數目`rParams`。</span><span class="sxs-lookup"><span data-stu-id="45e23-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45e23-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="45e23-112">Return Value</span></span>  
  
|<span data-ttu-id="45e23-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45e23-113">HRESULT</span></span>|<span data-ttu-id="45e23-114">描述</span><span class="sxs-lookup"><span data-stu-id="45e23-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="45e23-115">`EnumParams`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="45e23-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="45e23-116">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="45e23-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="45e23-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="45e23-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45e23-118">需求</span><span class="sxs-lookup"><span data-stu-id="45e23-118">Requirements</span></span>  
 <span data-ttu-id="45e23-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="45e23-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45e23-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="45e23-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45e23-121">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="45e23-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45e23-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45e23-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45e23-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="45e23-123">See Also</span></span>  
 [<span data-ttu-id="45e23-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="45e23-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="45e23-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="45e23-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
