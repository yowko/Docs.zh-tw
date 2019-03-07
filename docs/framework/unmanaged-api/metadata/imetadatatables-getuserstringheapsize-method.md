---
title: IMetaDataTables::GetUserStringHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1215da0816c1fc7cdfaee0da167118909f8e5eb3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466098"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="95031-102">IMetaDataTables::GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="95031-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="95031-103">取得大小，以位元組為單位的使用者字串堆積。</span><span class="sxs-lookup"><span data-stu-id="95031-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95031-104">語法</span><span class="sxs-lookup"><span data-stu-id="95031-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95031-105">參數</span><span class="sxs-lookup"><span data-stu-id="95031-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="95031-106">[out]大小 （位元組），使用者字串堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="95031-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95031-107">需求</span><span class="sxs-lookup"><span data-stu-id="95031-107">Requirements</span></span>  
 <span data-ttu-id="95031-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95031-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95031-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="95031-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95031-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="95031-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95031-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95031-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95031-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95031-112">See also</span></span>
- [<span data-ttu-id="95031-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="95031-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="95031-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="95031-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
