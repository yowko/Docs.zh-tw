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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954b4df6b341e18c5a995b57541a72e236278c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449591"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="9642c-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="9642c-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="9642c-103">取得指定資料列索引，在指定的資料表索引的資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="9642c-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9642c-104">語法</span><span class="sxs-lookup"><span data-stu-id="9642c-104">Syntax</span></span>  
  
```  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9642c-105">參數</span><span class="sxs-lookup"><span data-stu-id="9642c-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="9642c-106">[in]將從中擷取的資料列之資料表的索引。</span><span class="sxs-lookup"><span data-stu-id="9642c-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="9642c-107">[in]要取得的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="9642c-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="9642c-108">[out]指向資料列的指標。</span><span class="sxs-lookup"><span data-stu-id="9642c-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9642c-109">備註</span><span class="sxs-lookup"><span data-stu-id="9642c-109">Remarks</span></span>  
 <span data-ttu-id="9642c-110">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="9642c-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="9642c-111">如 GUID 資料表的相關資訊，請參閱 Common Language Infrastructure (CLI) 文件，尤其是 < 磁碟分割 II： 中繼資料定義和語意 >。</span><span class="sxs-lookup"><span data-stu-id="9642c-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="9642c-112">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](http://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="9642c-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9642c-113">需求</span><span class="sxs-lookup"><span data-stu-id="9642c-113">Requirements</span></span>  
 <span data-ttu-id="9642c-114">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9642c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9642c-115">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9642c-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9642c-116">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9642c-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9642c-117">**.NET framework 版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9642c-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9642c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9642c-118">See Also</span></span>  
 [<span data-ttu-id="9642c-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="9642c-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="9642c-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="9642c-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
