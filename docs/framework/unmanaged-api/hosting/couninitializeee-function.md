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
ms.openlocfilehash: 3531cfc0815c3f8a9479e35b2df60b2825801b39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136856"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="eb43d-102">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="eb43d-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="eb43d-103">`CoUninitializeEE` 已過時，而且沒有提供任何功能。</span><span class="sxs-lookup"><span data-stu-id="eb43d-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb43d-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb43d-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb43d-105">備註</span><span class="sxs-lookup"><span data-stu-id="eb43d-105">Remarks</span></span>  
 <span data-ttu-id="eb43d-106">無法從進程中卸載 common language runtime 執行引擎。</span><span class="sxs-lookup"><span data-stu-id="eb43d-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="eb43d-107">若要關閉執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。</span><span class="sxs-lookup"><span data-stu-id="eb43d-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb43d-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="eb43d-108">See also</span></span>

- [<span data-ttu-id="eb43d-109">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="eb43d-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)
- [<span data-ttu-id="eb43d-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="eb43d-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
