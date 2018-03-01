---
title: "CreateAssemblyCache 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e730ea9f83a40d92cb6a865fcdd87ebf523fe7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblycache-function"></a><span data-ttu-id="6f7a2-102">CreateAssemblyCache 函式</span><span class="sxs-lookup"><span data-stu-id="6f7a2-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="6f7a2-103">取得新的指標[IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)代表全域組件快取的執行個體。</span><span class="sxs-lookup"><span data-stu-id="6f7a2-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f7a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f7a2-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f7a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="6f7a2-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="6f7a2-106">[out]傳回`IAssemblyCache`指標。</span><span class="sxs-lookup"><span data-stu-id="6f7a2-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="6f7a2-107">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="6f7a2-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6f7a2-108">`dwReserved`必須是 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="6f7a2-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f7a2-109">需求</span><span class="sxs-lookup"><span data-stu-id="6f7a2-109">Requirements</span></span>  
 <span data-ttu-id="6f7a2-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f7a2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f7a2-111">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="6f7a2-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6f7a2-112">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6f7a2-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f7a2-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f7a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f7a2-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7a2-114">See Also</span></span>  
 [<span data-ttu-id="6f7a2-115">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="6f7a2-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="6f7a2-116">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6f7a2-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="6f7a2-117">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="6f7a2-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
