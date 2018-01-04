---
title: "IMetaDataTables2::GetMetaDataStorage 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables2.GetMetaDataStorage
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables2::GetMetaDataStorage
helpviewer_keywords:
- GetMetaDataStorage method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStorage method [.NET Framework metadata]
ms.assetid: 667a6d1e-753d-4ea2-8fd8-a8337d1bb9cd
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b00d03f8bd4a355d309f1a1266ca68f73647e0dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatables2getmetadatastorage-method"></a><span data-ttu-id="78967-102">IMetaDataTables2::GetMetaDataStorage 方法</span><span class="sxs-lookup"><span data-stu-id="78967-102">IMetaDataTables2::GetMetaDataStorage Method</span></span>
<span data-ttu-id="78967-103">取得大小與指定的區段中所儲存的中繼資料的內容。</span><span class="sxs-lookup"><span data-stu-id="78967-103">Gets the size and contents of the metadata stored in the specified section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78967-104">語法</span><span class="sxs-lookup"><span data-stu-id="78967-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataStorage (  
   [in, out] const void   **ppvMd,  
   [out] ULONG   *pcbMd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78967-105">參數</span><span class="sxs-lookup"><span data-stu-id="78967-105">Parameters</span></span>  
 `ppvMd`  
 <span data-ttu-id="78967-106">[in、 out]中繼資料區段指標。</span><span class="sxs-lookup"><span data-stu-id="78967-106">[in, out] A pointer to a metadata section.</span></span>  
  
 `pcbMd`  
 <span data-ttu-id="78967-107">[out]中繼資料資料流的大小。</span><span class="sxs-lookup"><span data-stu-id="78967-107">[out] The size of the metadata stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78967-108">需求</span><span class="sxs-lookup"><span data-stu-id="78967-108">Requirements</span></span>  
 <span data-ttu-id="78967-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="78967-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78967-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78967-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78967-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="78967-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78967-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78967-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78967-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="78967-113">See Also</span></span>  
 [<span data-ttu-id="78967-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="78967-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 [<span data-ttu-id="78967-115">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="78967-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
