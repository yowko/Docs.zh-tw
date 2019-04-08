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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc840df9dd0793a7347b7f0d8a05296a09d634c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192104"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="25b9b-102">IMetaDataEmit::SaveToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="25b9b-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="25b9b-103">將所有的中繼資料儲存在目前的範圍，以指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="25b9b-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="25b9b-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25b9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="25b9b-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="25b9b-106">[out]要開始寫入的中繼資料位址。</span><span class="sxs-lookup"><span data-stu-id="25b9b-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="25b9b-107">[in]以位元組為單位配置的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="25b9b-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b9b-108">需求</span><span class="sxs-lookup"><span data-stu-id="25b9b-108">Requirements</span></span>  
 <span data-ttu-id="25b9b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25b9b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b9b-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25b9b-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25b9b-111">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25b9b-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="25b9b-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="25b9b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="25b9b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25b9b-113">See also</span></span>

- [<span data-ttu-id="25b9b-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="25b9b-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="25b9b-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="25b9b-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
