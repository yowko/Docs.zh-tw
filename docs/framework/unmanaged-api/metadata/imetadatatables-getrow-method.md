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
ms.openlocfilehash: 71f6c496816fec1a7537f5ccdfdc1b47d17da871
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177109"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="21443-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="21443-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="21443-103">在指定的表索引的表中獲取指定行索引處的行。</span><span class="sxs-lookup"><span data-stu-id="21443-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21443-104">語法</span><span class="sxs-lookup"><span data-stu-id="21443-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21443-105">參數</span><span class="sxs-lookup"><span data-stu-id="21443-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="21443-106">[在]將從中檢索行的表的索引。</span><span class="sxs-lookup"><span data-stu-id="21443-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="21443-107">[在]要獲取的行的索引。</span><span class="sxs-lookup"><span data-stu-id="21443-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="21443-108">[出]指向行的指標。</span><span class="sxs-lookup"><span data-stu-id="21443-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21443-109">備註</span><span class="sxs-lookup"><span data-stu-id="21443-109">Remarks</span></span>  

  <span data-ttu-id="21443-110">我們不建議使用此方法，因為它不返回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="21443-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="21443-111">有關 GUID 表的資訊，請參閱通用語言基礎結構 （CLI） 文檔，尤其是"分區 II：元資料定義和語義"。</span><span class="sxs-lookup"><span data-stu-id="21443-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="21443-112">文檔可線上獲取;請參閱[ECMA C# 和通用語言基礎結構標準和](../../../standard/components.md#applicable-standards)[標準 ECMA-335 - 通用語言基礎結構 （CLI）。](http://www.ecma-international.org/publications/standards/Ecma-335.htm)</span><span class="sxs-lookup"><span data-stu-id="21443-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21443-113">需求</span><span class="sxs-lookup"><span data-stu-id="21443-113">Requirements</span></span>  
 <span data-ttu-id="21443-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21443-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21443-115">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="21443-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="21443-116">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="21443-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="21443-117">**.NET 框架版本**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21443-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21443-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21443-118">See also</span></span>

- [<span data-ttu-id="21443-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="21443-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="21443-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="21443-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
