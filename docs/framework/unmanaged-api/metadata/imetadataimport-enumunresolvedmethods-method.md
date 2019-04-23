---
title: IMetaDataImport::EnumUnresolvedMethods 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUnresolvedMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2e6e53f69f58c2f5778083d9b8f8be466b952cdd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090247"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="d194a-102">IMetaDataImport::EnumUnresolvedMethods 方法</span><span class="sxs-lookup"><span data-stu-id="d194a-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="d194a-103">列舉 MemberDef 語彙基元，其代表目前中繼資料範圍內無法解析的方法。</span><span class="sxs-lookup"><span data-stu-id="d194a-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d194a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d194a-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d194a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d194a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d194a-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="d194a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d194a-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="d194a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d194a-108">[out]陣列，用來儲存 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d194a-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d194a-109">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="d194a-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d194a-110">[out]MemberDef 語彙基元中傳回的數字`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="d194a-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d194a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="d194a-111">Return Value</span></span>  
  
|<span data-ttu-id="d194a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d194a-112">HRESULT</span></span>|<span data-ttu-id="d194a-113">描述</span><span class="sxs-lookup"><span data-stu-id="d194a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d194a-114">`EnumUnresolvedMethods` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="d194a-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d194a-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d194a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="d194a-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="d194a-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d194a-117">備註</span><span class="sxs-lookup"><span data-stu-id="d194a-117">Remarks</span></span>  
 <span data-ttu-id="d194a-118">無法解析的方法是指已宣告但未實作。</span><span class="sxs-lookup"><span data-stu-id="d194a-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="d194a-119">如果方法已標記為，方法包含在列舉`miForwardRef`任一個`mdPinvokeImpl`或`miRuntime`設為零。</span><span class="sxs-lookup"><span data-stu-id="d194a-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="d194a-120">換句話說，無法解析的方法是一種類別的方法標示為`miForwardRef`但它不實作 （連線到透過 PInvoke） 的 unmanaged 程式碼中也不會實作的執行階段本身內部</span><span class="sxs-lookup"><span data-stu-id="d194a-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="d194a-121">列舉型別會排除在模組範圍 （全域），或在介面或抽象類別中定義的所有方法。</span><span class="sxs-lookup"><span data-stu-id="d194a-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d194a-122">需求</span><span class="sxs-lookup"><span data-stu-id="d194a-122">Requirements</span></span>  
 <span data-ttu-id="d194a-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d194a-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d194a-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d194a-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d194a-125">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d194a-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d194a-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d194a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d194a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d194a-127">See also</span></span>

- [<span data-ttu-id="d194a-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="d194a-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d194a-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="d194a-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
