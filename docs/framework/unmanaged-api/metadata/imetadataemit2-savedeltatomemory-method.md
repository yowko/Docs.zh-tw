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
ms.openlocfilehash: 8a6f11996425c92d9b0e3123ee2d3a064739454b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492745"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="3b5e3-102">IMetaDataEmit2::SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="3b5e3-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="3b5e3-103">將目前的「編輯後繼續」會話的變更儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="3b5e3-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="3b5e3-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b5e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="3b5e3-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="3b5e3-106">脫銷要開始寫入中繼資料差異的位址。</span><span class="sxs-lookup"><span data-stu-id="3b5e3-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="3b5e3-107">在變更的大小。</span><span class="sxs-lookup"><span data-stu-id="3b5e3-107">[in] The size of the changes.</span></span> <span data-ttu-id="3b5e3-108">請使用[IMetaDataEmit2：： GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md)來判斷大小。</span><span class="sxs-lookup"><span data-stu-id="3b5e3-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b5e3-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="3b5e3-109">Requirements</span></span>  
 <span data-ttu-id="3b5e3-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b5e3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b5e3-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3b5e3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b5e3-112">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="3b5e3-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b5e3-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b5e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b5e3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b5e3-114">See also</span></span>

- [<span data-ttu-id="3b5e3-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="3b5e3-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="3b5e3-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="3b5e3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
