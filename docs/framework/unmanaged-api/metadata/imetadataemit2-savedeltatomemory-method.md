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
ms.openlocfilehash: 5ec4fe2a8e949cf6e9aa0ce68f4d4e49b72170b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177442"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="63c33-102">IMetaDataEmit2::SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="63c33-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="63c33-103">將更改從當前編輯和繼續會話保存到記憶體。</span><span class="sxs-lookup"><span data-stu-id="63c33-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c33-104">語法</span><span class="sxs-lookup"><span data-stu-id="63c33-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63c33-105">參數</span><span class="sxs-lookup"><span data-stu-id="63c33-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="63c33-106">[出]開始寫入中繼資料增量的位址。</span><span class="sxs-lookup"><span data-stu-id="63c33-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="63c33-107">[在]更改的大小。</span><span class="sxs-lookup"><span data-stu-id="63c33-107">[in] The size of the changes.</span></span> <span data-ttu-id="63c33-108">使用[IMetaDataEmit2：：獲取增量保存大小](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md)以確定大小。</span><span class="sxs-lookup"><span data-stu-id="63c33-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c33-109">需求</span><span class="sxs-lookup"><span data-stu-id="63c33-109">Requirements</span></span>  
 <span data-ttu-id="63c33-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="63c33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c33-111">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="63c33-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="63c33-112">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="63c33-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="63c33-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c33-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63c33-114">See also</span></span>

- [<span data-ttu-id="63c33-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="63c33-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="63c33-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="63c33-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
