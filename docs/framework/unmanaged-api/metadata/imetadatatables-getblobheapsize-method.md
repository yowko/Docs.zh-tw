---
title: "IMetaDataTables::GetBlobHeapSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetBlobHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 796a7246a90f60627906b1febb6fbe15152ed8e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="768ca-102">IMetaDataTables::GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="768ca-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="768ca-103">取得大小，單位為位元組的二進位大型物件 (BLOB) 堆積。</span><span class="sxs-lookup"><span data-stu-id="768ca-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="768ca-104">語法</span><span class="sxs-lookup"><span data-stu-id="768ca-104">Syntax</span></span>  
  
```  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="768ca-105">參數</span><span class="sxs-lookup"><span data-stu-id="768ca-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="768ca-106">[out]大小，以位元組為單位，對 BLOB 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="768ca-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="768ca-107">需求</span><span class="sxs-lookup"><span data-stu-id="768ca-107">Requirements</span></span>  
 <span data-ttu-id="768ca-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="768ca-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="768ca-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="768ca-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="768ca-110">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="768ca-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="768ca-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="768ca-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768ca-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="768ca-112">See Also</span></span>  
 [<span data-ttu-id="768ca-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="768ca-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="768ca-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="768ca-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
