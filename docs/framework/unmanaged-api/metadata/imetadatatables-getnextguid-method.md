---
title: IMetaDataTables::GetNextGuid 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextGuid
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextGuid
helpviewer_keywords:
- GetNextGuid method [.NET Framework metadata]
- IMetaDataTables::GetNextGuid method [.NET Framework metadata]
ms.assetid: 68f6ea4d-9112-4d6b-93d9-e34f1e2f2496
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b23e1d26d62012efe338eeb179db0e7ee17cd658
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042363"
---
# <a name="imetadatatablesgetnextguid-method"></a><span data-ttu-id="060c6-102">IMetaDataTables::GetNextGuid 方法</span><span class="sxs-lookup"><span data-stu-id="060c6-102">IMetaDataTables::GetNextGuid Method</span></span>
<span data-ttu-id="060c6-103">取得目前的資料表資料行中的下一個 GUID 值的索引。</span><span class="sxs-lookup"><span data-stu-id="060c6-103">Gets the index of the next GUID value in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="060c6-104">Syntax</span></span>  
  
```  
HRESULT GetNextGuid (  
    [in]  ULONG   ixGuid,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="060c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="060c6-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="060c6-106">[in]GUID 的資料表資料行的索引值。</span><span class="sxs-lookup"><span data-stu-id="060c6-106">[in] The index value from a GUID table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="060c6-107">[out]下一步 的 GUID 值的索引指標。</span><span class="sxs-lookup"><span data-stu-id="060c6-107">[out] A pointer to the index of the next GUID value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="060c6-108">備註</span><span class="sxs-lookup"><span data-stu-id="060c6-108">Remarks</span></span>  
 <span data-ttu-id="060c6-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="060c6-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="060c6-110">GUID 資料表的相關資訊，請參閱 Common Language Infrastructure (CLI) 文件，特別是 「 第二部分：中繼資料定義和語意 」。</span><span class="sxs-lookup"><span data-stu-id="060c6-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="060c6-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="060c6-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="060c6-112">需求</span><span class="sxs-lookup"><span data-stu-id="060c6-112">Requirements</span></span>  
 <span data-ttu-id="060c6-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="060c6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="060c6-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="060c6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="060c6-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="060c6-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="060c6-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="060c6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="060c6-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060c6-117">See also</span></span>

- [<span data-ttu-id="060c6-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="060c6-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="060c6-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="060c6-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
