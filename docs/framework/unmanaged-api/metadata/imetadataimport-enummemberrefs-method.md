---
title: IMetaDataImport::EnumMemberRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177338"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="6cd4c-102">IMetaDataImport::EnumMemberRefs 方法</span><span class="sxs-lookup"><span data-stu-id="6cd4c-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="6cd4c-103">列舉代表指定類型成員的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cd4c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cd4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cd4c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6cd4c-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="6cd4c-107">[在]要枚舉其成員的類型的類型的類型類型，TypeDef、TypeRef、方法Def或 ModuleRef 權杖。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="6cd4c-108">[出]用於存儲會員Ref權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6cd4c-109">[in] `rMemberRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6cd4c-110">[出]在 中`rMemberRefs`返回的會員Ref 權杖的實際數量。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cd4c-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cd4c-111">Return Value</span></span>  
  
|<span data-ttu-id="6cd4c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6cd4c-112">HRESULT</span></span>|<span data-ttu-id="6cd4c-113">描述</span><span class="sxs-lookup"><span data-stu-id="6cd4c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6cd4c-114">`EnumMemberRefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6cd4c-115">沒有要枚舉的會員Ref權杖。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="6cd4c-116">在這種情況下，`pcTokens`是零。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cd4c-117">需求</span><span class="sxs-lookup"><span data-stu-id="6cd4c-117">Requirements</span></span>  
 <span data-ttu-id="6cd4c-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cd4c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd4c-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="6cd4c-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cd4c-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6cd4c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd4c-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd4c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd4c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cd4c-122">See also</span></span>

- [<span data-ttu-id="6cd4c-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6cd4c-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6cd4c-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6cd4c-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
