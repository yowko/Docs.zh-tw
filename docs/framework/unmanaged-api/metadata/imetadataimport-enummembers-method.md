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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492030"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="ee2db-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="ee2db-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="ee2db-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ee2db-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee2db-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee2db-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee2db-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee2db-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ee2db-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="ee2db-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="ee2db-107">在TypeDef token，代表要列舉其成員的類型。</span><span class="sxs-lookup"><span data-stu-id="ee2db-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="ee2db-108">脫銷用來保存 MemberDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="ee2db-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ee2db-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ee2db-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ee2db-110">脫銷在中傳回的 MemberDef token 實際數目 `rMembers` 。</span><span class="sxs-lookup"><span data-stu-id="ee2db-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee2db-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee2db-111">Return Value</span></span>  
  
|<span data-ttu-id="ee2db-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ee2db-112">HRESULT</span></span>|<span data-ttu-id="ee2db-113">說明</span><span class="sxs-lookup"><span data-stu-id="ee2db-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ee2db-114">`EnumMembers`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="ee2db-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ee2db-115">沒有要列舉的 MemberDef token。</span><span class="sxs-lookup"><span data-stu-id="ee2db-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="ee2db-116">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="ee2db-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee2db-117">備註</span><span class="sxs-lookup"><span data-stu-id="ee2db-117">Remarks</span></span>  
 <span data-ttu-id="ee2db-118">列舉類別的成員集合時，只會傳回 `EnumMembers` 類別上直接定義的成員（欄位和方法，但**不會**傳回屬性或事件）。</span><span class="sxs-lookup"><span data-stu-id="ee2db-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="ee2db-119">它不會傳回類別所繼承的任何成員，即使類別提供這些繼承成員的執行。</span><span class="sxs-lookup"><span data-stu-id="ee2db-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="ee2db-120">若要列舉繼承的成員，呼叫者必須明確地引導繼承鏈。</span><span class="sxs-lookup"><span data-stu-id="ee2db-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="ee2db-121">請注意，繼承鏈的規則可能會根據發出原始中繼資料的語言或編譯器而有所不同。</span><span class="sxs-lookup"><span data-stu-id="ee2db-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="ee2db-122">不會列舉屬性和事件 `EnumMembers` 。</span><span class="sxs-lookup"><span data-stu-id="ee2db-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="ee2db-123">若要列舉這些，請使用[EnumProperties](imetadataimport-enumproperties-method.md)或[EnumEvents](imetadataimport-enumevents-method.md)。</span><span class="sxs-lookup"><span data-stu-id="ee2db-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="ee2db-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="ee2db-124">Requirements</span></span>  
 <span data-ttu-id="ee2db-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee2db-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2db-126">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ee2db-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee2db-127">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee2db-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ee2db-128">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2db-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2db-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee2db-129">See also</span></span>

- [<span data-ttu-id="ee2db-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ee2db-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ee2db-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ee2db-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
