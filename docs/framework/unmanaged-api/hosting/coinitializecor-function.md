---
title: CoInitializeCor 函式
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91315e8af0cc46a3450a7515b885988cffe34927
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429984"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="56c4f-102">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="56c4f-102">CoInitializeCor Function</span></span>
<span data-ttu-id="56c4f-103">`CoInitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="56c4f-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c4f-104">語法</span><span class="sxs-lookup"><span data-stu-id="56c4f-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="56c4f-105">備註</span><span class="sxs-lookup"><span data-stu-id="56c4f-105">Remarks</span></span>  
 <span data-ttu-id="56c4f-106">若要初始化 common language runtime，使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="56c4f-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c4f-107">需求</span><span class="sxs-lookup"><span data-stu-id="56c4f-107">Requirements</span></span>  
 <span data-ttu-id="56c4f-108">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="56c4f-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c4f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56c4f-109">See Also</span></span>  
 [<span data-ttu-id="56c4f-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="56c4f-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
