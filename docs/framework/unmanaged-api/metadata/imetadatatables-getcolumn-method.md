---
title: "IMetaDataTables::GetColumn 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumn
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 162162b972ab0e1f3de55d56c18372f2475c9846
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="f4b82-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="f4b82-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="f4b82-103">取得包含指定之資料行和指定的資料表中資料列的儲存格的值的指標。</span><span class="sxs-lookup"><span data-stu-id="f4b82-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4b82-104">語法</span><span class="sxs-lookup"><span data-stu-id="f4b82-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4b82-105">參數</span><span class="sxs-lookup"><span data-stu-id="f4b82-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="f4b82-106">[in]資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="f4b82-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="f4b82-107">[in]資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="f4b82-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="f4b82-108">[in]資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="f4b82-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="f4b82-109">[out]在儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="f4b82-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4b82-110">需求</span><span class="sxs-lookup"><span data-stu-id="f4b82-110">Requirements</span></span>  
 <span data-ttu-id="f4b82-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f4b82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b82-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4b82-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4b82-113">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="f4b82-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4b82-114">**.NET framework 版本**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b82-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b82-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4b82-115">See Also</span></span>  
 [<span data-ttu-id="f4b82-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="f4b82-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="f4b82-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="f4b82-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
