---
title: IMetaDataImport::EnumMembers 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: acb772a64c8f13405f2836bb5f4f308986dce414
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447651"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="97840-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="97840-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="97840-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="97840-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97840-104">語法</span><span class="sxs-lookup"><span data-stu-id="97840-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97840-105">參數</span><span class="sxs-lookup"><span data-stu-id="97840-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="97840-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="97840-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="97840-107">在TypeDef token，代表要列舉其成員的類型。</span><span class="sxs-lookup"><span data-stu-id="97840-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="97840-108">脫銷用來保存 MemberDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="97840-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="97840-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="97840-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="97840-110">脫銷`rMembers`中傳回的實際 MemberDef token 數目。</span><span class="sxs-lookup"><span data-stu-id="97840-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97840-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="97840-111">Return Value</span></span>  
  
|<span data-ttu-id="97840-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97840-112">HRESULT</span></span>|<span data-ttu-id="97840-113">描述</span><span class="sxs-lookup"><span data-stu-id="97840-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="97840-114">已成功傳回 `EnumMembers`。</span><span class="sxs-lookup"><span data-stu-id="97840-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="97840-115">沒有要列舉的 MemberDef token。</span><span class="sxs-lookup"><span data-stu-id="97840-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="97840-116">在此情況下，`pcTokens` 為零。</span><span class="sxs-lookup"><span data-stu-id="97840-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97840-117">備註</span><span class="sxs-lookup"><span data-stu-id="97840-117">Remarks</span></span>  
 <span data-ttu-id="97840-118">列舉類別的成員集合時，`EnumMembers` 只會傳回直接在類別上定義的成員（欄位和方法，但**不會**傳回屬性或事件）。</span><span class="sxs-lookup"><span data-stu-id="97840-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="97840-119">它不會傳回類別所繼承的任何成員，即使類別提供這些繼承成員的執行。</span><span class="sxs-lookup"><span data-stu-id="97840-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="97840-120">若要列舉繼承的成員，呼叫者必須明確地引導繼承鏈。</span><span class="sxs-lookup"><span data-stu-id="97840-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="97840-121">請注意，繼承鏈的規則可能會根據發出原始中繼資料的語言或編譯器而有所不同。</span><span class="sxs-lookup"><span data-stu-id="97840-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="97840-122">`EnumMembers`不會列舉屬性和事件。</span><span class="sxs-lookup"><span data-stu-id="97840-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="97840-123">若要列舉這些，請使用[EnumProperties](imetadataimport-enumproperties-method.md)或[EnumEvents](imetadataimport-enumevents-method.md)。</span><span class="sxs-lookup"><span data-stu-id="97840-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="97840-124">需求</span><span class="sxs-lookup"><span data-stu-id="97840-124">Requirements</span></span>  
 <span data-ttu-id="97840-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97840-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97840-126">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="97840-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97840-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97840-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97840-128">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97840-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97840-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="97840-129">See also</span></span>

- [<span data-ttu-id="97840-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="97840-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="97840-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="97840-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
