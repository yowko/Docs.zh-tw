---
title: "IMetaDataImport::EnumUnresolvedMethods 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumUnresolvedMethods
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumUnresolvedMethods
helpviewer_keywords:
- EnumUnresolvedMethods method [.NET Framework metadata]
- IMetaDataImport::EnumUnresolvedMethods method [.NET Framework metadata]
ms.assetid: eb3187d7-74cf-44b1-aeeb-7a8d2b60e3b7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3c7709180e5b7811379c25977f8a8d23b91adb3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="e2ab2-102">IMetaDataImport::EnumUnresolvedMethods 方法</span><span class="sxs-lookup"><span data-stu-id="e2ab2-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>
<span data-ttu-id="e2ab2-103">列舉 MemberDef 語彙基元，其代表目前中繼資料範圍內無法解析的方法。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ab2-104">語法</span><span class="sxs-lookup"><span data-stu-id="e2ab2-104">Syntax</span></span>  
  
```  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2ab2-105">參數</span><span class="sxs-lookup"><span data-stu-id="e2ab2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e2ab2-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e2ab2-107">這必須是 NULL 的第一個呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="e2ab2-108">[out]陣列，用來儲存 memberdef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e2ab2-109">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e2ab2-110">[out]Memberdef 語彙基元中傳回的數目`rMethods`。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2ab2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e2ab2-111">Return Value</span></span>  
  
|<span data-ttu-id="e2ab2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2ab2-112">HRESULT</span></span>|<span data-ttu-id="e2ab2-113">說明</span><span class="sxs-lookup"><span data-stu-id="e2ab2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e2ab2-114">`EnumUnresolvedMethods`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e2ab2-115">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="e2ab2-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ab2-117">備註</span><span class="sxs-lookup"><span data-stu-id="e2ab2-117">Remarks</span></span>  
 <span data-ttu-id="e2ab2-118">無法解析的方法是一種已宣告但未實作。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="e2ab2-119">方法會包含在列舉中如果方法已標記為`miForwardRef`和`mdPinvokeImpl`或`miRuntime`設為零。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="e2ab2-120">換句話說，無法解析的方法是標示的類別方法`miForwardRef`但這不是 （透過 PInvoke 到達） 的 unmanaged 程式碼中實作，或在內部實作的執行階段本身</span><span class="sxs-lookup"><span data-stu-id="e2ab2-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="e2ab2-121">列舉型別會排除在模組範圍 （全域） 或在介面或抽象類別所定義的所有方法。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ab2-122">需求</span><span class="sxs-lookup"><span data-stu-id="e2ab2-122">Requirements</span></span>  
 <span data-ttu-id="e2ab2-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e2ab2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ab2-124">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e2ab2-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2ab2-125">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e2ab2-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2ab2-126">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ab2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ab2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2ab2-127">See Also</span></span>  
 [<span data-ttu-id="e2ab2-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="e2ab2-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e2ab2-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="e2ab2-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
