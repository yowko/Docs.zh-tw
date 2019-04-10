---
title: IMetaDataImport::EnumParams 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumParams
helpviewer_keywords:
- IMetaDataImport::EnumParams method [.NET Framework metadata]
- EnumParams method [.NET Framework metadata]
ms.assetid: 52118dc9-fe6e-4b39-aa48-c3cc3ea4214d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed5ddd74e61e63426871f659aa1c962d38fd534
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221397"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="5dd91-102">IMetaDataImport::EnumParams 方法</span><span class="sxs-lookup"><span data-stu-id="5dd91-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="5dd91-103">列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="5dd91-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd91-104">語法</span><span class="sxs-lookup"><span data-stu-id="5dd91-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dd91-105">參數</span><span class="sxs-lookup"><span data-stu-id="5dd91-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5dd91-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="5dd91-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5dd91-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="5dd91-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="5dd91-108">[in]表示搭配參數來列舉方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5dd91-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="5dd91-109">[out]陣列，用來儲存 ParamDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5dd91-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5dd91-110">[in] `rParams` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="5dd91-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5dd91-111">[out]ParamDef 語彙基元中傳回的數字`rParams`。</span><span class="sxs-lookup"><span data-stu-id="5dd91-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dd91-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="5dd91-112">Return Value</span></span>  
  
|<span data-ttu-id="5dd91-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5dd91-113">HRESULT</span></span>|<span data-ttu-id="5dd91-114">描述</span><span class="sxs-lookup"><span data-stu-id="5dd91-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumParams` <span data-ttu-id="5dd91-115">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="5dd91-115">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5dd91-116">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5dd91-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="5dd91-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="5dd91-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5dd91-118">需求</span><span class="sxs-lookup"><span data-stu-id="5dd91-118">Requirements</span></span>  
 <span data-ttu-id="5dd91-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5dd91-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd91-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5dd91-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dd91-121">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="5dd91-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="5dd91-122">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5dd91-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5dd91-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5dd91-123">See also</span></span>

- [<span data-ttu-id="5dd91-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5dd91-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5dd91-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5dd91-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
