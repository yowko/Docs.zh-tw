---
title: "CoUninitializeCor 函式"
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
- CoUninitializeCor
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b9f50892b44cf8ce22cc126fe22323c8b0bbe6be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="couninitializecor-function"></a><span data-ttu-id="d27ff-102">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="d27ff-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="d27ff-103">`CoUninitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="d27ff-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d27ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="d27ff-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="d27ff-105">備註</span><span class="sxs-lookup"><span data-stu-id="d27ff-105">Remarks</span></span>  
 <span data-ttu-id="d27ff-106">Common language runtime 無法從處理序卸載。</span><span class="sxs-lookup"><span data-stu-id="d27ff-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="d27ff-107">若要完全移除執行的處理序的執行階段，您必須關閉該程序。</span><span class="sxs-lookup"><span data-stu-id="d27ff-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27ff-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="d27ff-108">See Also</span></span>  
 [<span data-ttu-id="d27ff-109">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d27ff-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
