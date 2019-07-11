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
ms.openlocfilehash: 3fee3c0b82bec102d8e292a76d3df5a14d40ace8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757666"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="d8af1-102">IMetaDataEmit::Merge 方法</span><span class="sxs-lookup"><span data-stu-id="d8af1-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="d8af1-103">將指定的匯入的範圍加入至要合併的範圍清單。</span><span class="sxs-lookup"><span data-stu-id="d8af1-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8af1-104">語法</span><span class="sxs-lookup"><span data-stu-id="d8af1-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8af1-105">參數</span><span class="sxs-lookup"><span data-stu-id="d8af1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="d8af1-106">[in]指標[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)可識別要合併之匯入的範圍的物件。</span><span class="sxs-lookup"><span data-stu-id="d8af1-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="d8af1-107">[in]指標[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)指定語彙基元重新對應的物件。</span><span class="sxs-lookup"><span data-stu-id="d8af1-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="d8af1-108">[in]指標[IUnknown](/cpp/atl/iunknown)指定錯誤的物件。</span><span class="sxs-lookup"><span data-stu-id="d8af1-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8af1-109">備註</span><span class="sxs-lookup"><span data-stu-id="d8af1-109">Remarks</span></span>  
 <span data-ttu-id="d8af1-110">呼叫[imetadataemit:: Mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)觸發的中繼資料合併成單一範圍。</span><span class="sxs-lookup"><span data-stu-id="d8af1-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8af1-111">需求</span><span class="sxs-lookup"><span data-stu-id="d8af1-111">Requirements</span></span>  
 <span data-ttu-id="d8af1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8af1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8af1-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8af1-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8af1-114">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d8af1-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8af1-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8af1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8af1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8af1-116">See also</span></span>

- [<span data-ttu-id="d8af1-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d8af1-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d8af1-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d8af1-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
