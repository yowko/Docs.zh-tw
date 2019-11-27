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
ms.openlocfilehash: 06894f238f9fda3111d5484bb1b2add183a5abb2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448065"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="fd0ea-102">IMetaDataEmit::Merge 方法</span><span class="sxs-lookup"><span data-stu-id="fd0ea-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="fd0ea-103">將指定的匯入範圍加入要合併的範圍清單。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd0ea-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd0ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd0ea-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="fd0ea-106">在[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件的指標，識別要合併的匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="fd0ea-107">在指定標記重新對應之[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="fd0ea-108">在指定錯誤之[IUnknown](/cpp/atl/iunknown)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd0ea-109">備註</span><span class="sxs-lookup"><span data-stu-id="fd0ea-109">Remarks</span></span>  
 <span data-ttu-id="fd0ea-110">呼叫[IMetaDataEmit：： MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)以觸發將中繼資料合併到單一範圍中。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0ea-111">需求</span><span class="sxs-lookup"><span data-stu-id="fd0ea-111">Requirements</span></span>  
 <span data-ttu-id="fd0ea-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd0ea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0ea-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="fd0ea-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd0ea-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="fd0ea-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd0ea-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0ea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0ea-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="fd0ea-116">See also</span></span>

- [<span data-ttu-id="fd0ea-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="fd0ea-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fd0ea-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="fd0ea-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
