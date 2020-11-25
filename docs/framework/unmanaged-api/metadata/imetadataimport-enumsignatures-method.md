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
ms.openlocfilehash: 3021124184ab0491337a07144e6f77b5bfea3681
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721968"
---
# <a name="imetadataimportenumsignatures-method"></a><span data-ttu-id="fa794-102">IMetaDataImport::EnumSignatures 方法</span><span class="sxs-lookup"><span data-stu-id="fa794-102">IMetaDataImport::EnumSignatures Method</span></span>

<span data-ttu-id="fa794-103">列舉代表目前範圍中獨立簽章的簽章語彙基元。</span><span class="sxs-lookup"><span data-stu-id="fa794-103">Enumerates Signature tokens representing stand-alone signatures in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa794-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa794-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumSignatures (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdSignature  rSignatures[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcSignatures  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa794-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa794-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="fa794-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="fa794-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="fa794-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="fa794-107">This must be NULL for the first call of this method.</span></span>  
  
 `rSignatures`  
 <span data-ttu-id="fa794-108">擴展用來儲存簽章標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="fa794-108">[out] The array used to store the Signature tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fa794-109">[in] `rSignatures` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="fa794-109">[in] The maximum size of the `rSignatures` array.</span></span>  
  
 `pcSignatures`  
 <span data-ttu-id="fa794-110">擴展傳回的簽章權杖數目 `rSignatures` 。</span><span class="sxs-lookup"><span data-stu-id="fa794-110">[out] The number of Signature tokens returned in `rSignatures`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa794-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="fa794-111">Return Value</span></span>  
  
|<span data-ttu-id="fa794-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fa794-112">HRESULT</span></span>|<span data-ttu-id="fa794-113">描述</span><span class="sxs-lookup"><span data-stu-id="fa794-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="fa794-114">`EnumSignatures` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="fa794-114">`EnumSignatures` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="fa794-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="fa794-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="fa794-116">在此情況下， `pcSignatures` 是零。</span><span class="sxs-lookup"><span data-stu-id="fa794-116">In that case, `pcSignatures` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa794-117">備註</span><span class="sxs-lookup"><span data-stu-id="fa794-117">Remarks</span></span>  

 <span data-ttu-id="fa794-118">簽章標記是由 [IMetaDataEmit：： GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) 方法所建立。</span><span class="sxs-lookup"><span data-stu-id="fa794-118">The Signature tokens are created by the [IMetaDataEmit::GetTokenFromSig](imetadataemit-gettokenfromsig-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa794-119">需求</span><span class="sxs-lookup"><span data-stu-id="fa794-119">Requirements</span></span>  

 <span data-ttu-id="fa794-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa794-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa794-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fa794-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa794-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="fa794-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa794-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa794-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa794-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa794-124">See also</span></span>

- [<span data-ttu-id="fa794-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="fa794-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="fa794-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="fa794-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
