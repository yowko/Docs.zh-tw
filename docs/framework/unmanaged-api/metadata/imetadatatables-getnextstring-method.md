---
title: "IMetaDataTables::GetNextString 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetNextString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9d9062ef164c5a50652ed78786725967fda999d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="4d92d-102">IMetaDataTables::GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="4d92d-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="4d92d-103">取得目前的資料表資料行中的下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="4d92d-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d92d-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d92d-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d92d-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d92d-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="4d92d-106">[in]字串資料表資料行的索引值。</span><span class="sxs-lookup"><span data-stu-id="4d92d-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="4d92d-107">[out]索引資料行中的下一個字串的指標。</span><span class="sxs-lookup"><span data-stu-id="4d92d-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d92d-108">需求</span><span class="sxs-lookup"><span data-stu-id="4d92d-108">Requirements</span></span>  
 <span data-ttu-id="4d92d-109">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d92d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d92d-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4d92d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d92d-111">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4d92d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d92d-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d92d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d92d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d92d-113">See Also</span></span>  
 [<span data-ttu-id="4d92d-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="4d92d-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="4d92d-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="4d92d-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
