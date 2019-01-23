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
ms.openlocfilehash: 438f2f58a4ce61d1757238fc46674611e4d677dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54508531"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="b4e42-102">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="b4e42-102">CoInitializeCor Function</span></span>
<span data-ttu-id="b4e42-103">`CoInitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="b4e42-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e42-104">語法</span><span class="sxs-lookup"><span data-stu-id="b4e42-104">Syntax</span></span>  
  
```  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b4e42-105">備註</span><span class="sxs-lookup"><span data-stu-id="b4e42-105">Remarks</span></span>  
 <span data-ttu-id="b4e42-106">若要初始化 common language runtime，使用任何一種[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或是[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="b4e42-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4e42-107">需求</span><span class="sxs-lookup"><span data-stu-id="b4e42-107">Requirements</span></span>  
 <span data-ttu-id="b4e42-108">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b4e42-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e42-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4e42-109">See also</span></span>
- [<span data-ttu-id="b4e42-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b4e42-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
