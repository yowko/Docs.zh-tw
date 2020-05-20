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
ms.openlocfilehash: 188f98504fa73c4a85615a4e688bae02d966b9b6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616745"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="d542d-102">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="d542d-102">CoInitializeCor Function</span></span>
<span data-ttu-id="d542d-103">`CoInitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="d542d-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d542d-104">語法</span><span class="sxs-lookup"><span data-stu-id="d542d-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d542d-105">備註</span><span class="sxs-lookup"><span data-stu-id="d542d-105">Remarks</span></span>  
 <span data-ttu-id="d542d-106">若要初始化 common language runtime，請使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="d542d-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d542d-107">需求</span><span class="sxs-lookup"><span data-stu-id="d542d-107">Requirements</span></span>  
 <span data-ttu-id="d542d-108">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d542d-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d542d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d542d-109">See also</span></span>

- [<span data-ttu-id="d542d-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d542d-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
