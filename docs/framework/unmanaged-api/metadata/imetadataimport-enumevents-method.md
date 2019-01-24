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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f205615db29878bcfe936e88cab26c3d5a8e3562
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514516"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="89103-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="89103-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="89103-103">列舉指定 TypeDef 語彙基元的事件定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="89103-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89103-104">語法</span><span class="sxs-lookup"><span data-stu-id="89103-104">Syntax</span></span>  
  
```  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89103-105">參數</span><span class="sxs-lookup"><span data-stu-id="89103-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="89103-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="89103-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="89103-107">[in]事件定義為要列舉的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="89103-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="89103-108">[out]傳回的事件陣列。</span><span class="sxs-lookup"><span data-stu-id="89103-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="89103-109">[in] `rEvents` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="89103-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="89103-110">[out]事件中傳回的實際數目`rEvents`。</span><span class="sxs-lookup"><span data-stu-id="89103-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89103-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="89103-111">Return Value</span></span>  
  
|<span data-ttu-id="89103-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89103-112">HRESULT</span></span>|<span data-ttu-id="89103-113">描述</span><span class="sxs-lookup"><span data-stu-id="89103-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="89103-114">`EnumEvents` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="89103-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="89103-115">沒有要列舉的事件。</span><span class="sxs-lookup"><span data-stu-id="89103-115">There are no events to enumerate.</span></span> <span data-ttu-id="89103-116">在此情況下，`pcEvents`為零。</span><span class="sxs-lookup"><span data-stu-id="89103-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89103-117">需求</span><span class="sxs-lookup"><span data-stu-id="89103-117">Requirements</span></span>  
 <span data-ttu-id="89103-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="89103-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89103-119">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89103-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89103-120">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="89103-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89103-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89103-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89103-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89103-122">See also</span></span>
- [<span data-ttu-id="89103-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="89103-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="89103-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="89103-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
