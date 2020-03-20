---
title: IMetaDataTables::GetGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type:
- apiref
ms.openlocfilehash: 57df124f15f78daad053d9634e1baa969a65cc35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175274"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="e282c-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="e282c-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="e282c-103">從指定索引處的行獲取 GUID。</span><span class="sxs-lookup"><span data-stu-id="e282c-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e282c-104">語法</span><span class="sxs-lookup"><span data-stu-id="e282c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e282c-105">參數</span><span class="sxs-lookup"><span data-stu-id="e282c-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="e282c-106">[在]要從中獲取 GUID 的行的索引。</span><span class="sxs-lookup"><span data-stu-id="e282c-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="e282c-107">[出]指向 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="e282c-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e282c-108">備註</span><span class="sxs-lookup"><span data-stu-id="e282c-108">Remarks</span></span>  

  <span data-ttu-id="e282c-109">我們不建議使用此方法，因為它不返回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="e282c-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="e282c-110">有關 GUID 表的資訊，請參閱通用語言基礎結構 （CLI） 文檔，尤其是"分區 II：元資料定義和語義"。</span><span class="sxs-lookup"><span data-stu-id="e282c-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="e282c-111">文檔可線上獲取;請參閱[ECMA C# 和通用語言基礎結構標準和](../../../standard/components.md#applicable-standards)[標準 ECMA-335 - 通用語言基礎結構 （CLI）。](http://www.ecma-international.org/publications/standards/Ecma-335.htm)</span><span class="sxs-lookup"><span data-stu-id="e282c-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e282c-112">需求</span><span class="sxs-lookup"><span data-stu-id="e282c-112">Requirements</span></span>  
 <span data-ttu-id="e282c-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e282c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e282c-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="e282c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e282c-115">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="e282c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e282c-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e282c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e282c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e282c-117">See also</span></span>

- [<span data-ttu-id="e282c-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="e282c-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="e282c-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="e282c-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
