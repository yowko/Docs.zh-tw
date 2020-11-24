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
ms.openlocfilehash: 01c4c1734aa0701f787a2b73787e9e4781901d42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672639"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="b6d49-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="b6d49-102">IMetaDataTables::GetRow Method</span></span>

<span data-ttu-id="b6d49-103">取得位於指定之資料表索引之資料表中指定之資料列索引處的資料列。</span><span class="sxs-lookup"><span data-stu-id="b6d49-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d49-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6d49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d49-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6d49-105">Parameters</span></span>  

 `ixTbl`  
 <span data-ttu-id="b6d49-106">在將從其中抓取資料列的資料表索引。</span><span class="sxs-lookup"><span data-stu-id="b6d49-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="b6d49-107">在要取得之資料列的索引。</span><span class="sxs-lookup"><span data-stu-id="b6d49-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="b6d49-108">擴展指向資料列之指標的指標。</span><span class="sxs-lookup"><span data-stu-id="b6d49-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6d49-109">備註</span><span class="sxs-lookup"><span data-stu-id="b6d49-109">Remarks</span></span>  

  <span data-ttu-id="b6d49-110">我們不建議使用此方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="b6d49-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="b6d49-111">如需有關 GUID 資料表的詳細資訊，請參閱通用語言基礎結構 (CLI) 檔，特別是「資料分割 II：元資料定義和語義」。</span><span class="sxs-lookup"><span data-stu-id="b6d49-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="b6d49-112">檔可在線上取得;請參閱 [ECMA c # 和通用語言基礎結構標準](../../../standard/components.md#applicable-standards) 以及 [標準 ECMA-335-通用語言基礎結構 (CLI) ](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。</span><span class="sxs-lookup"><span data-stu-id="b6d49-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d49-113">需求</span><span class="sxs-lookup"><span data-stu-id="b6d49-113">Requirements</span></span>  

 <span data-ttu-id="b6d49-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d49-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d49-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b6d49-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6d49-116">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b6d49-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6d49-117">**.NET Framework 版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d49-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d49-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d49-118">See also</span></span>

- [<span data-ttu-id="b6d49-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="b6d49-119">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="b6d49-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="b6d49-120">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
