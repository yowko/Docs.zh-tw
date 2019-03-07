---
title: IMetaDataTables::GetGuidHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0b41c03f5e6e08144ae566a3543d352c168555f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472105"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="d37e3-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="d37e3-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="d37e3-103">取得大小，以位元組為單位，GUID 堆積。</span><span class="sxs-lookup"><span data-stu-id="d37e3-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="d37e3-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d37e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="d37e3-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="d37e3-106">[out]大小 （位元組），GUID 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="d37e3-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d37e3-107">需求</span><span class="sxs-lookup"><span data-stu-id="d37e3-107">Requirements</span></span>  
 <span data-ttu-id="d37e3-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d37e3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37e3-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d37e3-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d37e3-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d37e3-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d37e3-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d37e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37e3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d37e3-112">See also</span></span>
- [<span data-ttu-id="d37e3-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="d37e3-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d37e3-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="d37e3-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
