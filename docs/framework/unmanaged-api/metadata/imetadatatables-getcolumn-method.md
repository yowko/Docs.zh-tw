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
ms.openlocfilehash: 850a97240e0a6450b4dec759a8786e0df5bffac8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448956"
---
# <a name="imetadatatablesgetcolumn-method"></a><span data-ttu-id="38c6a-102">IMetaDataTables::GetColumn 方法</span><span class="sxs-lookup"><span data-stu-id="38c6a-102">IMetaDataTables::GetColumn Method</span></span>
<span data-ttu-id="38c6a-103">取得包含指定之資料行和指定的資料表中資料列的儲存格的值的指標。</span><span class="sxs-lookup"><span data-stu-id="38c6a-103">Gets a pointer to the value contained in the cell of the specified column and row in the given table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38c6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="38c6a-104">Syntax</span></span>  
  
```  
HRESULT GetColumn (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38c6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="38c6a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="38c6a-106">[in]資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="38c6a-106">[in] The index of the table.</span></span>  
  
 `ixCol`  
 <span data-ttu-id="38c6a-107">[in]資料表中資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="38c6a-107">[in] The index of the column in the table.</span></span>  
  
 `rid`  
 <span data-ttu-id="38c6a-108">[in]資料表中的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="38c6a-108">[in] The index of the row in the table.</span></span>  
  
 `pVal`  
 <span data-ttu-id="38c6a-109">[out]在儲存格中值的指標。</span><span class="sxs-lookup"><span data-stu-id="38c6a-109">[out] A pointer to the value in the cell.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38c6a-110">需求</span><span class="sxs-lookup"><span data-stu-id="38c6a-110">Requirements</span></span>  
 <span data-ttu-id="38c6a-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38c6a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38c6a-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="38c6a-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38c6a-113">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="38c6a-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="38c6a-114">**.NET framework 版本** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38c6a-114">**.NET Framework Versions** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c6a-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38c6a-115">See Also</span></span>  
 [<span data-ttu-id="38c6a-116">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="38c6a-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="38c6a-117">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="38c6a-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
