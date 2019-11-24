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
ms.openlocfilehash: 743b6bed1a5d62f5214b8366b1a3c6e4ebecb98b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441712"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="9be74-102">IMetaDataImport::EnumMemberRefs 方法</span><span class="sxs-lookup"><span data-stu-id="9be74-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="9be74-103">列舉代表指定類型成員的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="9be74-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be74-104">語法</span><span class="sxs-lookup"><span data-stu-id="9be74-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be74-105">參數</span><span class="sxs-lookup"><span data-stu-id="9be74-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9be74-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="9be74-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="9be74-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="9be74-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="9be74-108">[out] The array used to store MemberRef tokens.</span><span class="sxs-lookup"><span data-stu-id="9be74-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9be74-109">[in] `rMemberRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="9be74-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="9be74-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="9be74-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9be74-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="9be74-111">Return Value</span></span>  
  
|<span data-ttu-id="9be74-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9be74-112">HRESULT</span></span>|<span data-ttu-id="9be74-113">描述</span><span class="sxs-lookup"><span data-stu-id="9be74-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9be74-114">`EnumMemberRefs` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="9be74-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9be74-115">There are no MemberRef tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="9be74-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="9be74-116">In that case, `pcTokens` is to zero.</span><span class="sxs-lookup"><span data-stu-id="9be74-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9be74-117">需求</span><span class="sxs-lookup"><span data-stu-id="9be74-117">Requirements</span></span>  
 <span data-ttu-id="9be74-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9be74-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be74-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9be74-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9be74-120">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9be74-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9be74-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be74-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be74-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="9be74-122">See also</span></span>

- [<span data-ttu-id="9be74-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="9be74-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9be74-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="9be74-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
