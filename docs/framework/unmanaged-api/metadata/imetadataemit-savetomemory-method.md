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
ms.openlocfilehash: e3ef09c98f22b03a9c4473505605f1688d4bbf17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612225"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="ee780-102">IMetaDataEmit::SaveToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="ee780-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="ee780-103">將所有的中繼資料儲存在目前的範圍，以指定的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="ee780-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee780-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee780-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee780-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee780-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="ee780-106">[out]要開始寫入的中繼資料位址。</span><span class="sxs-lookup"><span data-stu-id="ee780-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="ee780-107">[in]以位元組為單位配置的記憶體大小。</span><span class="sxs-lookup"><span data-stu-id="ee780-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee780-108">需求</span><span class="sxs-lookup"><span data-stu-id="ee780-108">Requirements</span></span>  
 <span data-ttu-id="ee780-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee780-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee780-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee780-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee780-111">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ee780-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee780-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee780-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee780-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee780-113">See also</span></span>
- [<span data-ttu-id="ee780-114">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="ee780-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ee780-115">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="ee780-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
