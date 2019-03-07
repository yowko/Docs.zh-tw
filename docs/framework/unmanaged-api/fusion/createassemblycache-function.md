---
title: CreateAssemblyCache 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6327c9d7dee548957a569b587faefe3d6d9cb1b9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497765"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="d3b8b-102">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="d3b8b-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="d3b8b-103">取得新指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)表示全域組件快取執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3b8b-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b8b-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3b8b-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3b8b-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3b8b-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="d3b8b-106">[out]傳回`IAssemblyCache`指標。</span><span class="sxs-lookup"><span data-stu-id="d3b8b-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="d3b8b-107">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="d3b8b-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d3b8b-108">`dwReserved` 必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="d3b8b-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b8b-109">需求</span><span class="sxs-lookup"><span data-stu-id="d3b8b-109">Requirements</span></span>  
 <span data-ttu-id="d3b8b-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3b8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b8b-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d3b8b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d3b8b-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d3b8b-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3b8b-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b8b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3b8b-114">See also</span></span>
- [<span data-ttu-id="d3b8b-115">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="d3b8b-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="d3b8b-116">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d3b8b-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="d3b8b-117">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="d3b8b-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
