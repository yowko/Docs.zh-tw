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
ms.openlocfilehash: 9d077d5c5a414568b5643cad0171e101d7bb06f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731705"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="3bb08-102">CoInitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="3bb08-102">CoInitializeCor Function</span></span>

<span data-ttu-id="3bb08-103">`CoInitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="3bb08-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bb08-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bb08-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3bb08-105">備註</span><span class="sxs-lookup"><span data-stu-id="3bb08-105">Remarks</span></span>  

 <span data-ttu-id="3bb08-106">若要初始化 common language runtime，請使用 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 或 [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)。</span><span class="sxs-lookup"><span data-stu-id="3bb08-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bb08-107">需求</span><span class="sxs-lookup"><span data-stu-id="3bb08-107">Requirements</span></span>  

 <span data-ttu-id="3bb08-108">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3bb08-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bb08-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bb08-109">See also</span></span>

- [<span data-ttu-id="3bb08-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3bb08-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
