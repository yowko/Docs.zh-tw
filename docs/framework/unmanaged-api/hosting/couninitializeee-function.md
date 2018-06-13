---
title: CoUninitializeEE 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
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
ms.openlocfilehash: 73fa281d28e9b5362ff386b55b07dd431f1915f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429178"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="b7de9-102">CoUninitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="b7de9-102">CoUninitializeEE Function</span></span>
<span data-ttu-id="b7de9-103">`CoUninitializeEE` 已經過時，不提供功能。</span><span class="sxs-lookup"><span data-stu-id="b7de9-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7de9-104">語法</span><span class="sxs-lookup"><span data-stu-id="b7de9-104">Syntax</span></span>  
  
```  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b7de9-105">備註</span><span class="sxs-lookup"><span data-stu-id="b7de9-105">Remarks</span></span>  
 <span data-ttu-id="b7de9-106">Common language runtime 執行引擎無法從處理序卸載。</span><span class="sxs-lookup"><span data-stu-id="b7de9-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="b7de9-107">若要關閉執行引擎呼叫[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)。</span><span class="sxs-lookup"><span data-stu-id="b7de9-107">To shut down the execution engine call [CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7de9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7de9-108">See Also</span></span>  
 [<span data-ttu-id="b7de9-109">CoInitializeEE 函式</span><span class="sxs-lookup"><span data-stu-id="b7de9-109">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 [<span data-ttu-id="b7de9-110">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b7de9-110">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
