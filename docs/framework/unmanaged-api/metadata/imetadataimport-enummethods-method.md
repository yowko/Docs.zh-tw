---
title: IMetaDataImport::EnumMethods 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6237951b7fab013a32a7e717215cacdbe1125b1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493702"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="410bc-102">IMetaDataImport::EnumMethods 方法</span><span class="sxs-lookup"><span data-stu-id="410bc-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="410bc-103">列舉代表指定類型方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="410bc-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="410bc-104">Syntax</span></span>  
  
```  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="410bc-105">參數</span><span class="sxs-lookup"><span data-stu-id="410bc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="410bc-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="410bc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="410bc-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="410bc-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="410bc-108">[in]TypeDef 語彙基元的方法來列舉表示的型別。</span><span class="sxs-lookup"><span data-stu-id="410bc-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="410bc-109">[out]要儲存 methoddef 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="410bc-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="410bc-110">[in]最大大小的 MethodDef`rMethods`陣列。</span><span class="sxs-lookup"><span data-stu-id="410bc-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="410bc-111">[out]中傳回的 methoddef 語彙基元數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="410bc-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="410bc-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="410bc-112">Return Value</span></span>  
  
|<span data-ttu-id="410bc-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="410bc-113">HRESULT</span></span>|<span data-ttu-id="410bc-114">描述</span><span class="sxs-lookup"><span data-stu-id="410bc-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="410bc-115">`EnumMethods` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="410bc-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="410bc-116">沒有列舉 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="410bc-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="410bc-117">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="410bc-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="410bc-118">需求</span><span class="sxs-lookup"><span data-stu-id="410bc-118">Requirements</span></span>  
 <span data-ttu-id="410bc-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="410bc-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410bc-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="410bc-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="410bc-121">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="410bc-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="410bc-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410bc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410bc-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="410bc-123">See also</span></span>
- [<span data-ttu-id="410bc-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="410bc-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="410bc-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="410bc-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
