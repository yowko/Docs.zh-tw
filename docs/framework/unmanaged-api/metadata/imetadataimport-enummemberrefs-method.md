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
ms.openlocfilehash: d8b02e85efc2cd7364690dd42104a313ba6ec272
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711451"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="2a4f9-102">IMetaDataImport::EnumMemberRefs 方法</span><span class="sxs-lookup"><span data-stu-id="2a4f9-102">IMetaDataImport::EnumMemberRefs Method</span></span>

<span data-ttu-id="2a4f9-103">列舉代表指定類型成員的 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4f9-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a4f9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a4f9-105">參數</span><span class="sxs-lookup"><span data-stu-id="2a4f9-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="2a4f9-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="2a4f9-107">在要列舉其成員之類型的 TypeDef、TypeRef、MethodDef 或 ModuleRef token。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="2a4f9-108">擴展用來儲存 MemberRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2a4f9-109">[in] `rMemberRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2a4f9-110">擴展在中傳回的實際 MemberRef 標記數目 `rMemberRefs` 。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a4f9-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="2a4f9-111">Return Value</span></span>  
  
|<span data-ttu-id="2a4f9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2a4f9-112">HRESULT</span></span>|<span data-ttu-id="2a4f9-113">描述</span><span class="sxs-lookup"><span data-stu-id="2a4f9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2a4f9-114">`EnumMemberRefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2a4f9-115">沒有要列舉的 MemberRef 標記。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="2a4f9-116">在此情況下， `pcTokens` 會是零。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2a4f9-117">需求</span><span class="sxs-lookup"><span data-stu-id="2a4f9-117">Requirements</span></span>  

 <span data-ttu-id="2a4f9-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a4f9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a4f9-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2a4f9-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2a4f9-120">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="2a4f9-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2a4f9-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a4f9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4f9-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a4f9-122">See also</span></span>

- [<span data-ttu-id="2a4f9-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2a4f9-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2a4f9-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2a4f9-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
