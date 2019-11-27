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
ms.openlocfilehash: 8e9e08ac903423b2e121f22cc9e43a660ccfac7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450093"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="f142e-102">IMetaDataImport::EnumMethods 方法</span><span class="sxs-lookup"><span data-stu-id="f142e-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="f142e-103">列舉代表指定類型方法的 MethodDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f142e-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f142e-104">語法</span><span class="sxs-lookup"><span data-stu-id="f142e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,   
   [in]  mdTypeDef      cl,   
   [out] mdMethodDef    rMethods[],   
   [in]  ULONG          cMax,   
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f142e-105">參數</span><span class="sxs-lookup"><span data-stu-id="f142e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f142e-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="f142e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="f142e-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="f142e-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="f142e-108">在TypeDef token，代表具有要列舉之方法的類型。</span><span class="sxs-lookup"><span data-stu-id="f142e-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="f142e-109">脫銷要儲存 MethodDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="f142e-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f142e-110">在MethodDef `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="f142e-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f142e-111">脫銷`rMethods`中傳回的 MethodDef 權杖數目。</span><span class="sxs-lookup"><span data-stu-id="f142e-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f142e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="f142e-112">Return Value</span></span>  
  
|<span data-ttu-id="f142e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f142e-113">HRESULT</span></span>|<span data-ttu-id="f142e-114">描述</span><span class="sxs-lookup"><span data-stu-id="f142e-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f142e-115">已成功傳回 `EnumMethods`。</span><span class="sxs-lookup"><span data-stu-id="f142e-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f142e-116">沒有要列舉的 MethodDef 標記。</span><span class="sxs-lookup"><span data-stu-id="f142e-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="f142e-117">在此情況下，`pcTokens` 為零。</span><span class="sxs-lookup"><span data-stu-id="f142e-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f142e-118">需求</span><span class="sxs-lookup"><span data-stu-id="f142e-118">Requirements</span></span>  
 <span data-ttu-id="f142e-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f142e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f142e-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f142e-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f142e-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f142e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f142e-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f142e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f142e-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f142e-123">See also</span></span>

- [<span data-ttu-id="f142e-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="f142e-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f142e-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="f142e-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
