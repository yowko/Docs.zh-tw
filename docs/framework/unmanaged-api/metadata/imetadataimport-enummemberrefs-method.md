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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c148ee0b2c96f2a387dac54eaff690ab3f05ebf8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447054"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="4da31-102">IMetaDataImport::EnumMemberRefs 方法</span><span class="sxs-lookup"><span data-stu-id="4da31-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="4da31-103">列舉代表指定類型成員的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4da31-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da31-104">語法</span><span class="sxs-lookup"><span data-stu-id="4da31-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4da31-105">參數</span><span class="sxs-lookup"><span data-stu-id="4da31-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4da31-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="4da31-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="4da31-107">[in]其成員的列舉的類型的 TypeDef 的 TypeRef、 MethodDef，ModuleRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4da31-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="4da31-108">[out]陣列，用來儲存 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4da31-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4da31-109">[in] `rMemberRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4da31-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4da31-110">[out]MemberRef 語彙基元中傳回的實際數目`rMemberRefs`。</span><span class="sxs-lookup"><span data-stu-id="4da31-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da31-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="4da31-111">Return Value</span></span>  
  
|<span data-ttu-id="4da31-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4da31-112">HRESULT</span></span>|<span data-ttu-id="4da31-113">描述</span><span class="sxs-lookup"><span data-stu-id="4da31-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4da31-114">`EnumMemberRefs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="4da31-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4da31-115">沒有列舉 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4da31-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="4da31-116">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="4da31-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4da31-117">需求</span><span class="sxs-lookup"><span data-stu-id="4da31-117">Requirements</span></span>  
 <span data-ttu-id="4da31-118">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4da31-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da31-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4da31-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4da31-120">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4da31-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4da31-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4da31-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da31-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da31-122">See Also</span></span>  
 [<span data-ttu-id="4da31-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4da31-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4da31-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4da31-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
