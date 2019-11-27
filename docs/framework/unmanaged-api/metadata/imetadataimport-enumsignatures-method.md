---
title: IMetaDataImport::EnumSignatures 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumSignatures
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumSignatures
helpviewer_keywords:
- EnumSignatures method [.NET Framework metadata]
- IMetaDataImport::EnumSignatures method [.NET Framework metadata]
ms.assetid: d0d65060-6f90-42a2-95cf-6ffb04352996
topic_type:
- apiref
ms.openlocfilehash: 9dbbdcc9d0fb9f0a8d2a64edfa4a0ad92570933c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450015"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="34f4d-102">IMetaDataImport::EnumSignatures 方法</span><span class="sxs-lookup"><span data-stu-id="34f4d-102">IMetaDataImport::EnumSignatures Method</span></span>
<span data-ttu-id="34f4d-103">列舉代表目前範圍中獨立簽章的簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="34f4d-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34f4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="34f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34f4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="34f4d-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="34f4d-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="34f4d-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="34f4d-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="34f4d-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="34f4d-108">脫銷用來儲存簽章標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="34f4d-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="34f4d-109">[in] `rSignatures` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="34f4d-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="34f4d-110">脫銷`rSignatures`中傳回的簽章權杖數目。</span><span class="sxs-lookup"><span data-stu-id="34f4d-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34f4d-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="34f4d-111">Return Value</span></span>  
  
|<span data-ttu-id="34f4d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34f4d-112">HRESULT</span></span>|<span data-ttu-id="34f4d-113">描述</span><span class="sxs-lookup"><span data-stu-id="34f4d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="34f4d-114">已成功傳回 `EnumSignatures`。</span><span class="sxs-lookup"><span data-stu-id="34f4d-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="34f4d-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="34f4d-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="34f4d-116">在此情況下，`pcSignatures` 為零。</span><span class="sxs-lookup"><span data-stu-id="34f4d-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34f4d-117">備註</span><span class="sxs-lookup"><span data-stu-id="34f4d-117">Remarks</span></span>  
 <span data-ttu-id="34f4d-118">簽章權杖是由[IMetaDataEmit：： GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md)方法所建立。</span><span class="sxs-lookup"><span data-stu-id="34f4d-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34f4d-119">需求</span><span class="sxs-lookup"><span data-stu-id="34f4d-119">Requirements</span></span>  
 <span data-ttu-id="34f4d-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34f4d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34f4d-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="34f4d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34f4d-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="34f4d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34f4d-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34f4d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f4d-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="34f4d-124">See also</span></span>

- [<span data-ttu-id="34f4d-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="34f4d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="34f4d-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="34f4d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
