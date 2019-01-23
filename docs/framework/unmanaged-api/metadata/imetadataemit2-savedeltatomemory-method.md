---
title: IMetaDataEmit2::SaveDeltaToMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84972388f90ea23032ed0524723d59077c732e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498891"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="c6e08-102">IMetaDataEmit2::SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="c6e08-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="c6e08-103">將目前的編輯和繼續工作階段的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="c6e08-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6e08-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6e08-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6e08-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6e08-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="c6e08-106">[out]要開始寫入的中繼資料差異位址。</span><span class="sxs-lookup"><span data-stu-id="c6e08-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="c6e08-107">[in]之變更的大小。</span><span class="sxs-lookup"><span data-stu-id="c6e08-107">[in] The size of the changes.</span></span> <span data-ttu-id="c6e08-108">使用[IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)決定的大小。</span><span class="sxs-lookup"><span data-stu-id="c6e08-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6e08-109">需求</span><span class="sxs-lookup"><span data-stu-id="c6e08-109">Requirements</span></span>  
 <span data-ttu-id="c6e08-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e08-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6e08-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c6e08-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c6e08-112">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="c6e08-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6e08-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6e08-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6e08-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6e08-114">See also</span></span>
- [<span data-ttu-id="c6e08-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c6e08-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c6e08-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c6e08-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
