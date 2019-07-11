---
title: CoInitializeCor 函式
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
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
ms.openlocfilehash: 7b2b7b89c73b59f4f735369659daabb6a8f88300
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779091"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="af6f3-102">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="af6f3-102">CoInitializeCor Function</span></span>
<span data-ttu-id="af6f3-103">`CoInitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="af6f3-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6f3-104">語法</span><span class="sxs-lookup"><span data-stu-id="af6f3-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="af6f3-105">備註</span><span class="sxs-lookup"><span data-stu-id="af6f3-105">Remarks</span></span>  
 <span data-ttu-id="af6f3-106">若要初始化 common language runtime，使用任何一種[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或是[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="af6f3-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af6f3-107">需求</span><span class="sxs-lookup"><span data-stu-id="af6f3-107">Requirements</span></span>  
 <span data-ttu-id="af6f3-108">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af6f3-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af6f3-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="af6f3-109">See also</span></span>

- [<span data-ttu-id="af6f3-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="af6f3-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
