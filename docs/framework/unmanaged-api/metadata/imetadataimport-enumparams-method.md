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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042587"
---
# <a name="imetadataimportenumparams-method"></a><span data-ttu-id="b431e-102">IMetaDataImport::EnumParams 方法</span><span class="sxs-lookup"><span data-stu-id="b431e-102">IMetaDataImport::EnumParams Method</span></span>
<span data-ttu-id="b431e-103">列舉 ParamDef 語彙基元，其代表指定 MethodDef 語彙基元所參考之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b431e-103">Enumerates ParamDef tokens representing the parameters of the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b431e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b431e-104">Syntax</span></span>  
  
```  
HRESULT EnumParams (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdMethodDef     mb,  
   [out] mdParamDef      rParams[],  
   [in]  ULONG           cMax,  
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b431e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b431e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b431e-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="b431e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b431e-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="b431e-107">This must be NULL for the first call of this method.</span></span>  
  
 `mb`  
 <span data-ttu-id="b431e-108">[in]表示搭配參數來列舉方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b431e-108">[in] A MethodDef token representing the method with the parameters to enumerate.</span></span>  
  
 `rParams`  
 <span data-ttu-id="b431e-109">[out]陣列，用來儲存 ParamDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b431e-109">[out] The array used to store the ParamDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b431e-110">[in] `rParams` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="b431e-110">[in] The maximum size of the `rParams` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b431e-111">[out]ParamDef 語彙基元中傳回的數字`rParams`。</span><span class="sxs-lookup"><span data-stu-id="b431e-111">[out] The number of ParamDef tokens returned in `rParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b431e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="b431e-112">Return Value</span></span>  
  
|<span data-ttu-id="b431e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b431e-113">HRESULT</span></span>|<span data-ttu-id="b431e-114">描述</span><span class="sxs-lookup"><span data-stu-id="b431e-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b431e-115">`EnumParams` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="b431e-115">`EnumParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b431e-116">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b431e-116">There are no tokens to enumerate.</span></span> <span data-ttu-id="b431e-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="b431e-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b431e-118">需求</span><span class="sxs-lookup"><span data-stu-id="b431e-118">Requirements</span></span>  
 <span data-ttu-id="b431e-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b431e-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b431e-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b431e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b431e-121">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b431e-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b431e-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b431e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b431e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b431e-123">See also</span></span>

- [<span data-ttu-id="b431e-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b431e-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b431e-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b431e-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
