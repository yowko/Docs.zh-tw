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
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501160"
---
# <a name="imetadatatablesgettableinfo-method"></a><span data-ttu-id="f959a-102">IMetaDataTables::GetTableInfo 方法</span><span class="sxs-lookup"><span data-stu-id="f959a-102">IMetaDataTables::GetTableInfo Method</span></span>
<span data-ttu-id="f959a-103">取得指定資料表的名稱、資料列大小、資料列數目、資料行數目和索引鍵資料行索引。</span><span class="sxs-lookup"><span data-stu-id="f959a-103">Gets the name, row size, number of rows, number of columns, and key column index of the specified table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f959a-104">語法</span><span class="sxs-lookup"><span data-stu-id="f959a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f959a-105">參數</span><span class="sxs-lookup"><span data-stu-id="f959a-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="f959a-106">在要傳回其屬性之資料表的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f959a-106">[in] The identifier of the table whose properties to return.</span></span>  
  
 `pcbRow`  
 <span data-ttu-id="f959a-107">脫銷資料表資料列大小（以位元組為單位）的指標。</span><span class="sxs-lookup"><span data-stu-id="f959a-107">[out] A pointer to the size, in bytes, of a table row.</span></span>  
  
 `pcRows`  
 <span data-ttu-id="f959a-108">脫銷資料表中的資料列數目指標。</span><span class="sxs-lookup"><span data-stu-id="f959a-108">[out] A pointer to the number of rows in the table.</span></span>  
  
 `pcCols`  
 <span data-ttu-id="f959a-109">脫銷資料表中的資料行數目指標。</span><span class="sxs-lookup"><span data-stu-id="f959a-109">[out] A pointer to the number of columns in the table.</span></span>  
  
 `piKey`  
 <span data-ttu-id="f959a-110">脫銷索引鍵資料行之索引的指標，如果資料表沒有索引鍵資料行，則為-1。</span><span class="sxs-lookup"><span data-stu-id="f959a-110">[out] A pointer to the index of the key column, or -1 if the table has no key column.</span></span>  
  
 `ppName`  
 <span data-ttu-id="f959a-111">脫銷指向資料表名稱之指標的指標。</span><span class="sxs-lookup"><span data-stu-id="f959a-111">[out] A pointer to a pointer to the table name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f959a-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="f959a-112">Requirements</span></span>  
 <span data-ttu-id="f959a-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f959a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f959a-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="f959a-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f959a-115">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="f959a-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f959a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f959a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f959a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f959a-117">See also</span></span>

- [<span data-ttu-id="f959a-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="f959a-118">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="f959a-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="f959a-119">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
