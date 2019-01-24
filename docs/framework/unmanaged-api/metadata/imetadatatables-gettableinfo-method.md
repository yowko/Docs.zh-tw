---
title: IMetaDataTables::GetTableInfo 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9bf3e5d427698673576f71e290fde54275b75317
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683452"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="51408-102">IMetaDataTables::GetTableInfo 方法</span><span class="sxs-lookup"><span data-stu-id="51408-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="51408-103">取得名稱、 資料列大小、 資料列數目、 資料行數與指定之資料表的索引鍵資料行索引。</span><span class="sxs-lookup"><span data-stu-id="51408-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51408-104">語法</span><span class="sxs-lookup"><span data-stu-id="51408-104">Syntax</span></span>  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="51408-105">參數</span><span class="sxs-lookup"><span data-stu-id="51408-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="51408-106">[in]資料表的識別碼傳回其屬性。</span><span class="sxs-lookup"><span data-stu-id="51408-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="51408-107">[out]大小 （位元組），資料表資料列的指標。</span><span class="sxs-lookup"><span data-stu-id="51408-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="51408-108">[out]在資料表中的資料列數目指標。</span><span class="sxs-lookup"><span data-stu-id="51408-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="51408-109">[out]在資料表中的資料行數目指標。</span><span class="sxs-lookup"><span data-stu-id="51408-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="51408-110">[out]索引鍵資料行或-1，如果資料表沒有索引鍵資料行的索引指標。</span><span class="sxs-lookup"><span data-stu-id="51408-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="51408-111">[out]指向資料表名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="51408-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51408-112">需求</span><span class="sxs-lookup"><span data-stu-id="51408-112">Requirements</span></span>  
 <span data-ttu-id="51408-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="51408-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51408-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="51408-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51408-115">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="51408-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="51408-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51408-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51408-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51408-117">See also</span></span>
- [<span data-ttu-id="51408-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="51408-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="51408-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="51408-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
