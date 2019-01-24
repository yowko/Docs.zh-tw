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
ms.openlocfilehash: a88acf59043613bb216ffe84dfb1593bd6ebea00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651886"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="03871-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="03871-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="03871-103">取得在指定的資料行和給定資料表中的資料列的資料格中所包含的值的指標。</span><span class="sxs-lookup"><span data-stu-id="03871-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03871-104">語法</span><span class="sxs-lookup"><span data-stu-id="03871-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03871-105">參數</span><span class="sxs-lookup"><span data-stu-id="03871-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="03871-106">[in]資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="03871-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="03871-107">[in]在資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="03871-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="03871-108">[in]在資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="03871-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="03871-109">[out]在儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="03871-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03871-110">需求</span><span class="sxs-lookup"><span data-stu-id="03871-110">Requirements</span></span>  
 <span data-ttu-id="03871-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03871-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03871-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03871-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03871-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03871-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03871-114">**.NET framework 版本** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03871-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03871-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03871-115">See also</span></span>
- [<span data-ttu-id="03871-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="03871-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="03871-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="03871-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
