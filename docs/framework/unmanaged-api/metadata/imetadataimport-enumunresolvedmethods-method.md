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
ms.openlocfilehash: 6b5e7bbe2303a200d7829fea12e228a513595f97
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716547"
---
# <a name="imetadataimportenumunresolvedmethods-method"></a><span data-ttu-id="dabbc-102">IMetaDataImport::EnumUnresolvedMethods 方法</span><span class="sxs-lookup"><span data-stu-id="dabbc-102">IMetaDataImport::EnumUnresolvedMethods Method</span></span>

<span data-ttu-id="dabbc-103">列舉 MemberDef 語彙基元，其代表目前中繼資料範圍內無法解析的方法。</span><span class="sxs-lookup"><span data-stu-id="dabbc-103">Enumerates MemberDef tokens representing the unresolved methods in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="dabbc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumUnresolvedMethods (  
   [in, out] HCORENUM    *phEnum,  
   [out]     mdToken     rMethods[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dabbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="dabbc-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="dabbc-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="dabbc-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="dabbc-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="dabbc-107">This must be NULL for the first call of this method.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="dabbc-108">擴展用來儲存 MemberDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="dabbc-108">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="dabbc-109">[in] `rMethods` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="dabbc-109">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dabbc-110">擴展傳回的 MemberDef 權杖數目 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="dabbc-110">[out] The number of MemberDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dabbc-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="dabbc-111">Return Value</span></span>  
  
|<span data-ttu-id="dabbc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dabbc-112">HRESULT</span></span>|<span data-ttu-id="dabbc-113">描述</span><span class="sxs-lookup"><span data-stu-id="dabbc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="dabbc-114">`EnumUnresolvedMethods` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="dabbc-114">`EnumUnresolvedMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="dabbc-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="dabbc-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="dabbc-116">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="dabbc-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dabbc-117">備註</span><span class="sxs-lookup"><span data-stu-id="dabbc-117">Remarks</span></span>  

 <span data-ttu-id="dabbc-118">未解析的方法是已宣告但未執行的方法。</span><span class="sxs-lookup"><span data-stu-id="dabbc-118">An unresolved method is one that has been declared but not implemented.</span></span> <span data-ttu-id="dabbc-119">如果方法標示為 `miForwardRef` ，而且 `mdPinvokeImpl` 或 `miRuntime` 設定為零，則方法會包含在列舉中。</span><span class="sxs-lookup"><span data-stu-id="dabbc-119">A method is included in the enumeration if the method is marked `miForwardRef` and either `mdPinvokeImpl` or `miRuntime` is set to zero.</span></span> <span data-ttu-id="dabbc-120">換句話說，未解析的方法是標示為 `miForwardRef` 但未在非受控程式碼中執行的類別方法 (透過 PInvoke) ，也不是由執行時間本身內部執行</span><span class="sxs-lookup"><span data-stu-id="dabbc-120">In other words, an unresolved method is a class method that is marked `miForwardRef` but which is not implemented in unmanaged code (reached via PInvoke) nor implemented internally by the runtime itself</span></span>  
  
 <span data-ttu-id="dabbc-121">列舉會排除在模組範圍 (globals) 或在介面或抽象類別中定義的所有方法。</span><span class="sxs-lookup"><span data-stu-id="dabbc-121">The enumeration excludes all methods that are defined either at module scope (globals) or in interfaces or abstract classes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dabbc-122">需求</span><span class="sxs-lookup"><span data-stu-id="dabbc-122">Requirements</span></span>  

 <span data-ttu-id="dabbc-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dabbc-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dabbc-124">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="dabbc-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dabbc-125">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="dabbc-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dabbc-126">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dabbc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabbc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dabbc-127">See also</span></span>

- [<span data-ttu-id="dabbc-128">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="dabbc-128">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dabbc-129">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="dabbc-129">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
