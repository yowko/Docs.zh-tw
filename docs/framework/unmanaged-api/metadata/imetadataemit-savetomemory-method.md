---
title: IMetaDataEmit::SaveToMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177574"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="b9470-102">IMetaDataEmit::SaveToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="b9470-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="b9470-103">將當前作用域中的所有中繼資料保存到指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="b9470-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9470-104">語法</span><span class="sxs-lookup"><span data-stu-id="b9470-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9470-105">參數</span><span class="sxs-lookup"><span data-stu-id="b9470-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="b9470-106">[出]開始寫入中繼資料的位址。</span><span class="sxs-lookup"><span data-stu-id="b9470-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="b9470-107">[在]已分配記憶體的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="b9470-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9470-108">需求</span><span class="sxs-lookup"><span data-stu-id="b9470-108">Requirements</span></span>  
 <span data-ttu-id="b9470-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b9470-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9470-110">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b9470-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9470-111">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b9470-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b9470-112">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9470-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9470-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9470-113">See also</span></span>

- [<span data-ttu-id="b9470-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b9470-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b9470-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b9470-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
