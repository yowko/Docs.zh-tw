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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1075643bbd17765bf33a26038fc6beaf32d0aebb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781497"
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="10fb5-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="10fb5-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="10fb5-103">從指定索引處的資料列中取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="10fb5-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10fb5-104">語法</span><span class="sxs-lookup"><span data-stu-id="10fb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10fb5-105">參數</span><span class="sxs-lookup"><span data-stu-id="10fb5-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="10fb5-106">[in]若要取得 GUID 的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="10fb5-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="10fb5-107">[out]GUID 指標的指標。</span><span class="sxs-lookup"><span data-stu-id="10fb5-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10fb5-108">備註</span><span class="sxs-lookup"><span data-stu-id="10fb5-108">Remarks</span></span>  
 <span data-ttu-id="10fb5-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="10fb5-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="10fb5-110">GUID 資料表的相關資訊，請參閱 Common Language Infrastructure (CLI) 文件，特別是 「 第二部分：中繼資料定義和語意 」。</span><span class="sxs-lookup"><span data-stu-id="10fb5-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="10fb5-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](https://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="10fb5-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10fb5-112">需求</span><span class="sxs-lookup"><span data-stu-id="10fb5-112">Requirements</span></span>  
 <span data-ttu-id="10fb5-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10fb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10fb5-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="10fb5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="10fb5-115">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="10fb5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="10fb5-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10fb5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10fb5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10fb5-117">See also</span></span>

- [<span data-ttu-id="10fb5-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="10fb5-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="10fb5-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="10fb5-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
