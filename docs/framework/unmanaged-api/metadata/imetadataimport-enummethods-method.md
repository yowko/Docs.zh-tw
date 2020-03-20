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
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177300"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="d5b6a-102">IMetaDataImport::EnumMethods 方法</span><span class="sxs-lookup"><span data-stu-id="d5b6a-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="d5b6a-103">列舉代表指定類型方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5b6a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5b6a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d5b6a-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d5b6a-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="d5b6a-108">[在]表示具有要枚舉的方法的類型的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d5b6a-109">[出]要存儲方法Def權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d5b6a-110">[在]方法Def`rMethods`陣列的最大大小。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d5b6a-111">[出]在 中`rMethods`返回的 MethodDef 權杖數。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5b6a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="d5b6a-112">Return Value</span></span>  
  
|<span data-ttu-id="d5b6a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d5b6a-113">HRESULT</span></span>|<span data-ttu-id="d5b6a-114">描述</span><span class="sxs-lookup"><span data-stu-id="d5b6a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d5b6a-115">`EnumMethods`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d5b6a-116">沒有要枚舉的 MethodDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="d5b6a-117">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5b6a-118">需求</span><span class="sxs-lookup"><span data-stu-id="d5b6a-118">Requirements</span></span>  
 <span data-ttu-id="d5b6a-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5b6a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b6a-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="d5b6a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d5b6a-121">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="d5b6a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d5b6a-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b6a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b6a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5b6a-123">See also</span></span>

- [<span data-ttu-id="d5b6a-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d5b6a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d5b6a-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d5b6a-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
