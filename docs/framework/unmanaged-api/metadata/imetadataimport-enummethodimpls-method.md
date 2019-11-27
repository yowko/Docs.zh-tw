---
title: IMetaDataImport::EnumMethodImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
ms.openlocfilehash: 193e8788d5a1b28f43f2fb0d4d935a18542dd923
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427498"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="07c62-102">IMetaDataImport::EnumMethodImpls 方法</span><span class="sxs-lookup"><span data-stu-id="07c62-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="07c62-103">列舉代表指定類型方法的 MethodBody 和 MethodDeclaration 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="07c62-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c62-104">語法</span><span class="sxs-lookup"><span data-stu-id="07c62-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07c62-105">參數</span><span class="sxs-lookup"><span data-stu-id="07c62-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="07c62-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="07c62-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="07c62-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="07c62-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="07c62-108">在要列舉其方法實作為之類型的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="07c62-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="07c62-109">脫銷要儲存 MethodBody token 的陣列。</span><span class="sxs-lookup"><span data-stu-id="07c62-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="07c62-110">脫銷要儲存 Ethoddeclaration token 的陣列。</span><span class="sxs-lookup"><span data-stu-id="07c62-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="07c62-111">在`rMethodBody` 和 `rMethodDecl` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="07c62-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="07c62-112">在`rMethodBody` 和 `rMethodDecl`中傳回的實際方法數目。</span><span class="sxs-lookup"><span data-stu-id="07c62-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07c62-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="07c62-113">Return Value</span></span>  
  
|<span data-ttu-id="07c62-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07c62-114">HRESULT</span></span>|<span data-ttu-id="07c62-115">描述</span><span class="sxs-lookup"><span data-stu-id="07c62-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="07c62-116">已成功傳回 `EnumMethodImpls`。</span><span class="sxs-lookup"><span data-stu-id="07c62-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="07c62-117">沒有要列舉的方法權杖。</span><span class="sxs-lookup"><span data-stu-id="07c62-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="07c62-118">在此情況下，`pcTokens` 為零。</span><span class="sxs-lookup"><span data-stu-id="07c62-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="07c62-119">需求</span><span class="sxs-lookup"><span data-stu-id="07c62-119">Requirements</span></span>  
 <span data-ttu-id="07c62-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07c62-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c62-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="07c62-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07c62-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="07c62-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07c62-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07c62-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c62-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="07c62-124">See also</span></span>

- [<span data-ttu-id="07c62-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="07c62-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="07c62-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="07c62-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
