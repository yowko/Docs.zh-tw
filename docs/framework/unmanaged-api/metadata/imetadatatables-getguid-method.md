---
title: "IMetaDataTables::GetGuid 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetGuid
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetGuid
helpviewer_keywords:
- GetGuid method [.NET Framework metadata]
- IMetaDataTables::GetGuid method [.NET Framework metadata]
ms.assetid: a3546316-e24d-417f-9909-e45d42c9d471
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 52b96fbe582a5c8e1818462a5e28970dbaf50605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetguid-method"></a><span data-ttu-id="b3276-102">IMetaDataTables::GetGuid 方法</span><span class="sxs-lookup"><span data-stu-id="b3276-102">IMetaDataTables::GetGuid Method</span></span>
<span data-ttu-id="b3276-103">從指定索引處的資料列取得的 GUID。</span><span class="sxs-lookup"><span data-stu-id="b3276-103">Gets a GUID from the row at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3276-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3276-104">Syntax</span></span>  
  
```  
HRESULT GetGuid (   
    [in]  ULONG       ixGuid,  
    [out] const GUID  **ppGUID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3276-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3276-105">Parameters</span></span>  
 `ixGuid`  
 <span data-ttu-id="b3276-106">[in]要取得 GUID 的資料列索引。</span><span class="sxs-lookup"><span data-stu-id="b3276-106">[in] The index of the row from which to get the GUID.</span></span>  
  
 `ppGuid`  
 <span data-ttu-id="b3276-107">[out]指標至 GUID 的指標。</span><span class="sxs-lookup"><span data-stu-id="b3276-107">[out] A pointer to a pointer to the GUID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3276-108">備註</span><span class="sxs-lookup"><span data-stu-id="b3276-108">Remarks</span></span>  
 <span data-ttu-id="b3276-109">我們不建議使用這個方法，因為它不會傳回一致的結果。</span><span class="sxs-lookup"><span data-stu-id="b3276-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="b3276-110">如 GUID 資料表的相關資訊，請參閱 Common Language Infrastructure (CLI) 文件，尤其是 < 磁碟分割 II： 中繼資料定義和語意 >。</span><span class="sxs-lookup"><span data-stu-id="b3276-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="b3276-111">您可以線上取得這份文件；請參閱 MSDN 上的 [ECMA C# 和通用語言基礎結構標準](http://go.microsoft.com/fwlink/?LinkID=99212)，以及 Ecma International 網站上的[標準 ECMA-335 - 通用語言基礎結構 (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="b3276-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3276-112">需求</span><span class="sxs-lookup"><span data-stu-id="b3276-112">Requirements</span></span>  
 <span data-ttu-id="b3276-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3276-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3276-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3276-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3276-115">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3276-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3276-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3276-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3276-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3276-117">See Also</span></span>  
 [<span data-ttu-id="b3276-118">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="b3276-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b3276-119">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="b3276-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
