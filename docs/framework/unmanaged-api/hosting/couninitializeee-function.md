---
title: CoUninitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c4e22c2e80af37177294d86c2e5775a5c296fe7
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211854"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="dc70a-102">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="dc70a-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="dc70a-103">`CoUninitializeEE` 已經過時，不提供功能。</span><span class="sxs-lookup"><span data-stu-id="dc70a-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc70a-104">語法</span><span class="sxs-lookup"><span data-stu-id="dc70a-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="dc70a-105">備註</span><span class="sxs-lookup"><span data-stu-id="dc70a-105">Remarks</span></span>  
 <span data-ttu-id="dc70a-106">Common language runtime 執行引擎無法從處理序卸載。</span><span class="sxs-lookup"><span data-stu-id="dc70a-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="dc70a-107">若要關閉的執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。</span><span class="sxs-lookup"><span data-stu-id="dc70a-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc70a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc70a-108">See also</span></span>
- [<span data-ttu-id="dc70a-109">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="dc70a-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="dc70a-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="dc70a-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
