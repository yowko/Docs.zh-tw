---
title: IMetaDataTables::GetBlobHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f9f49219b810ac85b1f021c206bfab21d11a055
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745956"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="ff4ce-102">IMetaDataTables::GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="ff4ce-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="ff4ce-103">取得大小，以位元組為單位的二進位大型物件 (BLOB) 堆積。</span><span class="sxs-lookup"><span data-stu-id="ff4ce-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff4ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff4ce-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff4ce-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff4ce-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="ff4ce-106">[out]大小 （位元組），對 BLOB 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="ff4ce-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff4ce-107">需求</span><span class="sxs-lookup"><span data-stu-id="ff4ce-107">Requirements</span></span>  
 <span data-ttu-id="ff4ce-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff4ce-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff4ce-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ff4ce-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ff4ce-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="ff4ce-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff4ce-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff4ce-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4ce-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff4ce-112">See also</span></span>
- [<span data-ttu-id="ff4ce-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ff4ce-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ff4ce-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ff4ce-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
