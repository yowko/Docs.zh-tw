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
ms.openlocfilehash: be4fb0b4b49408a97b318e0f54f5a753f3f24ef1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435804"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="75f35-102">IMetaDataEmit::SaveToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="75f35-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="75f35-103">將目前範圍中的所有中繼資料儲存至指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="75f35-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75f35-104">語法</span><span class="sxs-lookup"><span data-stu-id="75f35-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75f35-105">參數</span><span class="sxs-lookup"><span data-stu-id="75f35-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="75f35-106">脫銷要開始寫入中繼資料的位址。</span><span class="sxs-lookup"><span data-stu-id="75f35-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="75f35-107">在配置的記憶體大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="75f35-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75f35-108">需求</span><span class="sxs-lookup"><span data-stu-id="75f35-108">Requirements</span></span>  
 <span data-ttu-id="75f35-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="75f35-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75f35-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="75f35-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="75f35-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="75f35-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75f35-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75f35-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75f35-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75f35-113">See also</span></span>

- [<span data-ttu-id="75f35-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="75f35-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="75f35-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="75f35-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
