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
ms.openlocfilehash: 4faf8646b81f92ddf65eff15fdc610d275b37864
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440018"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="81547-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="81547-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="81547-103">列舉指定 TypeDef 語彙基元的事件定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="81547-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81547-104">語法</span><span class="sxs-lookup"><span data-stu-id="81547-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81547-105">參數</span><span class="sxs-lookup"><span data-stu-id="81547-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="81547-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="81547-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="81547-107">[in] The TypeDef token whose event definitions are to be enumerated.</span><span class="sxs-lookup"><span data-stu-id="81547-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="81547-108">[out] The array of returned events.</span><span class="sxs-lookup"><span data-stu-id="81547-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="81547-109">[in] `rEvents` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="81547-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="81547-110">[out] The actual number of events returned in `rEvents`.</span><span class="sxs-lookup"><span data-stu-id="81547-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81547-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="81547-111">Return Value</span></span>  
  
|<span data-ttu-id="81547-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81547-112">HRESULT</span></span>|<span data-ttu-id="81547-113">描述</span><span class="sxs-lookup"><span data-stu-id="81547-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="81547-114">`EnumEvents` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="81547-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="81547-115">There are no events to enumerate.</span><span class="sxs-lookup"><span data-stu-id="81547-115">There are no events to enumerate.</span></span> <span data-ttu-id="81547-116">In that case, `pcEvents` is zero.</span><span class="sxs-lookup"><span data-stu-id="81547-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="81547-117">需求</span><span class="sxs-lookup"><span data-stu-id="81547-117">Requirements</span></span>  
 <span data-ttu-id="81547-118">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="81547-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81547-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="81547-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81547-120">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81547-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81547-121">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81547-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81547-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="81547-122">See also</span></span>

- [<span data-ttu-id="81547-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="81547-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="81547-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="81547-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
