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
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175703"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="f3fbc-102">IMetaDataEmit::Merge 方法</span><span class="sxs-lookup"><span data-stu-id="f3fbc-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="f3fbc-103">將指定的導入作用域添加到要合併的範圍清單中。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3fbc-104">語法</span><span class="sxs-lookup"><span data-stu-id="f3fbc-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3fbc-105">參數</span><span class="sxs-lookup"><span data-stu-id="f3fbc-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="f3fbc-106">[在]指向[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)物件的指標，用於標識要合併的導入作用域。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="f3fbc-107">[在]指向[IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)物件的指標，用於指定權杖重新映射。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="f3fbc-108">[在]指向指定錯誤的[IUnknown](/cpp/atl/iunknown)物件的指標。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3fbc-109">備註</span><span class="sxs-lookup"><span data-stu-id="f3fbc-109">Remarks</span></span>  
 <span data-ttu-id="f3fbc-110">調用[IMetaDataEmit：：合併結束](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md)以觸發將中繼資料合併到單個作用域中。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3fbc-111">需求</span><span class="sxs-lookup"><span data-stu-id="f3fbc-111">Requirements</span></span>  
 <span data-ttu-id="f3fbc-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3fbc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3fbc-113">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="f3fbc-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3fbc-114">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f3fbc-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3fbc-115">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3fbc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fbc-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3fbc-116">See also</span></span>

- [<span data-ttu-id="f3fbc-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="f3fbc-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f3fbc-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="f3fbc-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
