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
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="a5384-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="a5384-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="a5384-103">列舉代表指定類型成員的 MemberDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a5384-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5384-104">語法</span><span class="sxs-lookup"><span data-stu-id="a5384-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5384-105">參數</span><span class="sxs-lookup"><span data-stu-id="a5384-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a5384-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="a5384-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a5384-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="a5384-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="a5384-108">[out] The array used to hold the MemberDef tokens.</span><span class="sxs-lookup"><span data-stu-id="a5384-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a5384-109">[in] `rMembers` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="a5384-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a5384-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="a5384-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5384-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a5384-111">Return Value</span></span>  
  
|<span data-ttu-id="a5384-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a5384-112">HRESULT</span></span>|<span data-ttu-id="a5384-113">描述</span><span class="sxs-lookup"><span data-stu-id="a5384-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a5384-114">`EnumMembers` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="a5384-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a5384-115">There are no MemberDef tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="a5384-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="a5384-116">In that case, `pcTokens` is zero.</span><span class="sxs-lookup"><span data-stu-id="a5384-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5384-117">備註</span><span class="sxs-lookup"><span data-stu-id="a5384-117">Remarks</span></span>  
 <span data-ttu-id="a5384-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span><span class="sxs-lookup"><span data-stu-id="a5384-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="a5384-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span><span class="sxs-lookup"><span data-stu-id="a5384-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="a5384-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span><span class="sxs-lookup"><span data-stu-id="a5384-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="a5384-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span><span class="sxs-lookup"><span data-stu-id="a5384-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="a5384-122">Properties and events are not enumerated by `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="a5384-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="a5384-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5384-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="a5384-124">需求</span><span class="sxs-lookup"><span data-stu-id="a5384-124">Requirements</span></span>  
 <span data-ttu-id="a5384-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a5384-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5384-126">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a5384-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5384-127">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5384-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a5384-128">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5384-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5384-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="a5384-129">See also</span></span>

- [<span data-ttu-id="a5384-130">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a5384-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a5384-131">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a5384-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
