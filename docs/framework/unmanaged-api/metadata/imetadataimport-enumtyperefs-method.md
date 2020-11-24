---
title: IMetaDataImport::EnumTypeRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: e77520552eea9b58e4358cc5928e5ce666037009
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678151"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="76cf2-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="76cf2-102">IMetaDataImport::EnumTypeRefs Method</span></span>

<span data-ttu-id="76cf2-103">列舉在目前中繼資料範圍中定義的 TypeRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="76cf2-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76cf2-104">語法</span><span class="sxs-lookup"><span data-stu-id="76cf2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76cf2-105">參數</span><span class="sxs-lookup"><span data-stu-id="76cf2-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="76cf2-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="76cf2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="76cf2-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="76cf2-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="76cf2-108">擴展用來儲存 TypeRef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="76cf2-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="76cf2-109">[in] `rTypeRefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="76cf2-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="76cf2-110">擴展傳回之 TypeRef token 數目的指標 `rTypeRefs` 。</span><span class="sxs-lookup"><span data-stu-id="76cf2-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76cf2-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="76cf2-111">Return Value</span></span>  
  
|<span data-ttu-id="76cf2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76cf2-112">HRESULT</span></span>|<span data-ttu-id="76cf2-113">描述</span><span class="sxs-lookup"><span data-stu-id="76cf2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="76cf2-114">`EnumTypeRefs` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="76cf2-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="76cf2-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="76cf2-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="76cf2-116">在此情況下， `pcTypeRefs` 是零。</span><span class="sxs-lookup"><span data-stu-id="76cf2-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76cf2-117">備註</span><span class="sxs-lookup"><span data-stu-id="76cf2-117">Remarks</span></span>  

 <span data-ttu-id="76cf2-118">TypeRef 標記代表類型的參考。</span><span class="sxs-lookup"><span data-stu-id="76cf2-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76cf2-119">需求</span><span class="sxs-lookup"><span data-stu-id="76cf2-119">Requirements</span></span>  

 <span data-ttu-id="76cf2-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="76cf2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76cf2-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="76cf2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76cf2-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="76cf2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76cf2-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76cf2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cf2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76cf2-124">See also</span></span>

- [<span data-ttu-id="76cf2-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="76cf2-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="76cf2-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="76cf2-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
