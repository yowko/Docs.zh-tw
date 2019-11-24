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
ms.openlocfilehash: 9973ef77a064dfe144d742d8cf12d8ae8dd2565f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447407"
---
# <a name="imetadatatablesgetrow-method"></a><span data-ttu-id="ae0e6-102">IMetaDataTables::GetRow 方法</span><span class="sxs-lookup"><span data-stu-id="ae0e6-102">IMetaDataTables::GetRow Method</span></span>
<span data-ttu-id="ae0e6-103">Gets the row at the specified row index, in the table at the specified table index.</span><span class="sxs-lookup"><span data-stu-id="ae0e6-103">Gets the row at the specified row index, in the table at the specified table index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae0e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRow (   
    [in]  ULONG   ixTbl,  
    [in]  ULONG   rid,  
    [out] void    **ppRow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae0e6-105">Parameters</span></span>  
 `ixTbl`  
 <span data-ttu-id="ae0e6-106">[in] The index of the table from which the row will be retrieved.</span><span class="sxs-lookup"><span data-stu-id="ae0e6-106">[in] The index of the table from which the row will be retrieved.</span></span>  
  
 `rid`  
 <span data-ttu-id="ae0e6-107">[in] The index of the row to get.</span><span class="sxs-lookup"><span data-stu-id="ae0e6-107">[in] The index of the row to get.</span></span>  
  
 `ppRow`  
 <span data-ttu-id="ae0e6-108">[out] A pointer to a pointer to the row.</span><span class="sxs-lookup"><span data-stu-id="ae0e6-108">[out] A pointer to a pointer to the row.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae0e6-109">備註</span><span class="sxs-lookup"><span data-stu-id="ae0e6-109">Remarks</span></span>  
 <span data-ttu-id="ae0e6-110">We do not recommend the use of this method, because it does not return consistent results.</span><span class="sxs-lookup"><span data-stu-id="ae0e6-110">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="ae0e6-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span><span class="sxs-lookup"><span data-stu-id="ae0e6-111">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="ae0e6-112">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-112">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0e6-113">需求</span><span class="sxs-lookup"><span data-stu-id="ae0e6-113">Requirements</span></span>  
 <span data-ttu-id="ae0e6-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae0e6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae0e6-115">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae0e6-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae0e6-116">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae0e6-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae0e6-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae0e6-117">**.NET Framework Versions**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0e6-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="ae0e6-118">See also</span></span>

- [<span data-ttu-id="ae0e6-119">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ae0e6-119">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="ae0e6-120">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ae0e6-120">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
