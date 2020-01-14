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
ms.openlocfilehash: 9ac6eba18ae23dc80a8dc90383aa67cfe41b39ff
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937411"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="96aad-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="96aad-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="96aad-103">在指定之資料表索引的資料表中，取得位於指定資料列索引處的資料列。</span><span class="sxs-lookup"><span data-stu-id="96aad-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96aad-104">語法</span><span class="sxs-lookup"><span data-stu-id="96aad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96aad-105">參數</span><span class="sxs-lookup"><span data-stu-id="96aad-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="96aad-106">在將從中抓取資料列的資料表索引。</span><span class="sxs-lookup"><span data-stu-id="96aad-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="96aad-107">在要取得的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="96aad-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="96aad-108">脫銷資料列指標的指標。</span><span class="sxs-lookup"><span data-stu-id="96aad-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96aad-109">備註</span><span class="sxs-lookup"><span data-stu-id="96aad-109">Remarks</span></span>  

  <span data-ttu-id="96aad-110">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="96aad-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="96aad-111">如需 GUID 資料表的詳細資訊，請參閱通用語言基礎結構（CLI）檔，特別是「分割區 II：元資料定義和語法」。</span><span class="sxs-lookup"><span data-stu-id="96aad-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="96aad-112">檔可從線上取得;請[參閱C# ECMA 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards)和[標準 Ecma-335-通用語言基礎結構（CLI）](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="96aad-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96aad-113">需求</span><span class="sxs-lookup"><span data-stu-id="96aad-113">Requirements</span></span>  
 <span data-ttu-id="96aad-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96aad-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96aad-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="96aad-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96aad-116">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="96aad-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96aad-117">**.NET Framework 版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96aad-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96aad-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="96aad-118">See also</span></span>

- [<span data-ttu-id="96aad-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="96aad-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="96aad-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="96aad-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
