---
title: IMetaDataEmit::Merge 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 899f2ca5ef1b987687f5c065ad3e1965e142d103
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43743962"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="c3372-102">IMetaDataEmit::Merge 方法</span><span class="sxs-lookup"><span data-stu-id="c3372-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="c3372-103">將指定的匯入的範圍加入至要合併的範圍清單。</span><span class="sxs-lookup"><span data-stu-id="c3372-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3372-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3372-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3372-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3372-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="c3372-106">[in]指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)可識別要合併之匯入的範圍的物件。</span><span class="sxs-lookup"><span data-stu-id="c3372-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="c3372-107">[in]指標[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)指定語彙基元重新對應的物件。</span><span class="sxs-lookup"><span data-stu-id="c3372-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="c3372-108">[in]指標[IUnknown](/cpp/atl/iunknown)指定錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="c3372-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3372-109">備註</span><span class="sxs-lookup"><span data-stu-id="c3372-109">Remarks</span></span>  
 <span data-ttu-id="c3372-110">呼叫[imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)觸發的中繼資料合併成單一範圍。</span><span class="sxs-lookup"><span data-stu-id="c3372-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3372-111">需求</span><span class="sxs-lookup"><span data-stu-id="c3372-111">Requirements</span></span>  
 <span data-ttu-id="c3372-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3372-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3372-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3372-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3372-114">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c3372-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3372-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3372-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3372-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3372-116">See Also</span></span>  
 [<span data-ttu-id="c3372-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c3372-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c3372-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c3372-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
