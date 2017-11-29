---
title: "IMetaDataTables::GetGuidHeapSize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuidHeapSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 76a2aa4495a9f34a57c8a84ec40ab946abc64532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="87f79-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="87f79-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="87f79-103">取得以位元組為單位 GUID 堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="87f79-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f79-104">語法</span><span class="sxs-lookup"><span data-stu-id="87f79-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87f79-105">參數</span><span class="sxs-lookup"><span data-stu-id="87f79-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="87f79-106">[out]大小，以位元組為單位 GUID 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="87f79-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f79-107">需求</span><span class="sxs-lookup"><span data-stu-id="87f79-107">Requirements</span></span>  
 <span data-ttu-id="87f79-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="87f79-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f79-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="87f79-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87f79-110">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="87f79-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="87f79-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f79-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f79-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87f79-112">See Also</span></span>  
 [<span data-ttu-id="87f79-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="87f79-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="87f79-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="87f79-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
