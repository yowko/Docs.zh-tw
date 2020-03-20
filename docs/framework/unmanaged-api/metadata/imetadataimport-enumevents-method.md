---
title: IMetaDataImport::EnumEvents 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: bd50d63b1f7080f510c29f90979b7b36242af1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177377"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="ec5e7-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="ec5e7-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="ec5e7-103">列舉指定 TypeDef 語彙基元的事件定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec5e7-104">語法</span><span class="sxs-lookup"><span data-stu-id="ec5e7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec5e7-105">參數</span><span class="sxs-lookup"><span data-stu-id="ec5e7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ec5e7-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="ec5e7-107">[在]要枚舉事件定義的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="ec5e7-108">[出]返回的事件的陣列。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ec5e7-109">[in] `rEvents` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="ec5e7-110">[出]在 中`rEvents`返回的事件的實際數。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec5e7-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="ec5e7-111">Return Value</span></span>  
  
|<span data-ttu-id="ec5e7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec5e7-112">HRESULT</span></span>|<span data-ttu-id="ec5e7-113">描述</span><span class="sxs-lookup"><span data-stu-id="ec5e7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ec5e7-114">`EnumEvents`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ec5e7-115">沒有要枚舉的事件。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-115">There are no events to enumerate.</span></span> <span data-ttu-id="ec5e7-116">在這種情況下，`pcEvents`為零。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec5e7-117">需求</span><span class="sxs-lookup"><span data-stu-id="ec5e7-117">Requirements</span></span>  
 <span data-ttu-id="ec5e7-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ec5e7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec5e7-119">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="ec5e7-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec5e7-120">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ec5e7-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec5e7-121">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec5e7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec5e7-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec5e7-122">See also</span></span>

- [<span data-ttu-id="ec5e7-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="ec5e7-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ec5e7-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="ec5e7-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
