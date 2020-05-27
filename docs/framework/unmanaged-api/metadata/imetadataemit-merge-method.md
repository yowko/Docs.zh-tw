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
ms.openlocfilehash: e7fe5cbe27c0771a71e4c03d14ab68ada7d0741a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004162"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="91602-102">IMetaDataEmit::Merge 方法</span><span class="sxs-lookup"><span data-stu-id="91602-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="91602-103">將指定的匯入範圍加入要合併的範圍清單。</span><span class="sxs-lookup"><span data-stu-id="91602-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91602-104">語法</span><span class="sxs-lookup"><span data-stu-id="91602-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91602-105">參數</span><span class="sxs-lookup"><span data-stu-id="91602-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="91602-106">在[IMetaDataImport](imetadataimport-interface.md)物件的指標，識別要合併的匯入範圍。</span><span class="sxs-lookup"><span data-stu-id="91602-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="91602-107">在指定標記重新對應之[IMapToken](imaptoken-interface.md)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="91602-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="91602-108">在指定錯誤之[IUnknown](/cpp/atl/iunknown)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="91602-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91602-109">備註</span><span class="sxs-lookup"><span data-stu-id="91602-109">Remarks</span></span>  
 <span data-ttu-id="91602-110">呼叫[IMetaDataEmit：： MergeEnd](imetadataemit-mergeend-method.md)以觸發將中繼資料合併到單一範圍中。</span><span class="sxs-lookup"><span data-stu-id="91602-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91602-111">需求</span><span class="sxs-lookup"><span data-stu-id="91602-111">Requirements</span></span>  
 <span data-ttu-id="91602-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91602-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91602-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="91602-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91602-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="91602-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91602-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91602-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91602-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91602-116">See also</span></span>

- [<span data-ttu-id="91602-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="91602-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="91602-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="91602-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
