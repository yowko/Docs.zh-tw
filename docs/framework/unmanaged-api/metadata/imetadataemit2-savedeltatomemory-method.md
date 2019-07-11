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
ms.openlocfilehash: 79b21613ba844ca4c749d9c04d75260e326e6512
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777137"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="a4119-102">IMetaDataEmit2::SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="a4119-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="a4119-103">將目前的編輯和繼續工作階段的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="a4119-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4119-104">語法</span><span class="sxs-lookup"><span data-stu-id="a4119-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4119-105">參數</span><span class="sxs-lookup"><span data-stu-id="a4119-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="a4119-106">[out]要開始寫入的中繼資料差異位址。</span><span class="sxs-lookup"><span data-stu-id="a4119-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="a4119-107">[in]之變更的大小。</span><span class="sxs-lookup"><span data-stu-id="a4119-107">[in] The size of the changes.</span></span> <span data-ttu-id="a4119-108">使用[IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)決定的大小。</span><span class="sxs-lookup"><span data-stu-id="a4119-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4119-109">需求</span><span class="sxs-lookup"><span data-stu-id="a4119-109">Requirements</span></span>  
 <span data-ttu-id="a4119-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a4119-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4119-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a4119-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4119-112">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a4119-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4119-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4119-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4119-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4119-114">See also</span></span>

- [<span data-ttu-id="a4119-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a4119-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="a4119-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a4119-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
