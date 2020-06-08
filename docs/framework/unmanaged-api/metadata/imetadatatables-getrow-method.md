---
title: IMetaDataTables::GetRow 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetRow
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetRow
helpviewer_keywords:
- IMetaDataTables::GetRow method [.NET Framework metadata]
- GetRow method [.NET Framework metadata]
ms.assetid: a7408d51-0bce-45a2-b58f-da4660bbc039
topic_type:
- apiref
ms.openlocfilehash: 13d514157382c75a2eb9799837f9355d0e469c99
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489895"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="0abca-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="0abca-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="0abca-103">在指定之資料表索引的資料表中，取得位於指定資料列索引處的資料列。</span><span class="sxs-lookup"><span data-stu-id="0abca-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abca-104">語法</span><span class="sxs-lookup"><span data-stu-id="0abca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0abca-105">參數</span><span class="sxs-lookup"><span data-stu-id="0abca-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="0abca-106">在將從中抓取資料列的資料表索引。</span><span class="sxs-lookup"><span data-stu-id="0abca-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="0abca-107">在要取得的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="0abca-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="0abca-108">脫銷資料列指標的指標。</span><span class="sxs-lookup"><span data-stu-id="0abca-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0abca-109">備註</span><span class="sxs-lookup"><span data-stu-id="0abca-109">Remarks</span></span>  

  <span data-ttu-id="0abca-110">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="0abca-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="0abca-111">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="0abca-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="0abca-112">檔可從線上取得;請參閱[ECMA c # 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards)和[標準 ecma-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="0abca-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0abca-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="0abca-113">Requirements</span></span>  
 <span data-ttu-id="0abca-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0abca-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0abca-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="0abca-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0abca-116">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="0abca-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0abca-117">**.NET Framework 版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0abca-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abca-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0abca-118">See also</span></span>

- [<span data-ttu-id="0abca-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="0abca-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="0abca-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="0abca-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
