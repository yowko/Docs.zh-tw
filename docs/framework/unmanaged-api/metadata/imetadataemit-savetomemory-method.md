---
title: "IMetaDataEmit::SaveToMemory 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b88034562701508369d6aadef8e92e31b2de438c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="67618-102">IMetaDataEmit::SaveToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="67618-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="67618-103">指定的記憶體區域目前範圍中儲存所有的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="67618-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67618-104">語法</span><span class="sxs-lookup"><span data-stu-id="67618-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67618-105">參數</span><span class="sxs-lookup"><span data-stu-id="67618-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="67618-106">[out]要開始寫入中繼資料位址。</span><span class="sxs-lookup"><span data-stu-id="67618-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="67618-107">[in]以位元組為單位配置的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="67618-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67618-108">需求</span><span class="sxs-lookup"><span data-stu-id="67618-108">Requirements</span></span>  
 <span data-ttu-id="67618-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67618-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67618-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="67618-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67618-111">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="67618-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67618-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67618-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67618-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="67618-113">See Also</span></span>  
 [<span data-ttu-id="67618-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="67618-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="67618-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="67618-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
