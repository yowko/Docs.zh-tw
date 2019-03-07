---
title: IMetaDataTables::GetColumn 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c380d363830eb6b4c47110d50cdb4d08e4568d8
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499806"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="14285-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="14285-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="14285-103">取得在指定的資料行和給定資料表中的資料列的資料格中所包含的值的指標。</span><span class="sxs-lookup"><span data-stu-id="14285-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14285-104">語法</span><span class="sxs-lookup"><span data-stu-id="14285-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14285-105">參數</span><span class="sxs-lookup"><span data-stu-id="14285-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="14285-106">[in]資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="14285-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="14285-107">[in]在資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="14285-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="14285-108">[in]在資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="14285-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="14285-109">[out]在儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="14285-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14285-110">需求</span><span class="sxs-lookup"><span data-stu-id="14285-110">Requirements</span></span>  
 <span data-ttu-id="14285-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="14285-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14285-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="14285-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="14285-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="14285-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="14285-114">**.NET framework 版本** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14285-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14285-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14285-115">See also</span></span>
- [<span data-ttu-id="14285-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="14285-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="14285-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="14285-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
