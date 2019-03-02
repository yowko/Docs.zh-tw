---
title: CoUninitializeCor 函式
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dca4fd4a4d20627bef8f7fedd5a801ba07e8e19b
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212075"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="6df66-102">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="6df66-102">CoUninitializeCor Function</span></span>
<span data-ttu-id="6df66-103">`CoUninitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="6df66-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df66-104">語法</span><span class="sxs-lookup"><span data-stu-id="6df66-104">Syntax</span></span>  
  
```  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="6df66-105">備註</span><span class="sxs-lookup"><span data-stu-id="6df66-105">Remarks</span></span>  
 <span data-ttu-id="6df66-106">Common language runtime 無法從處理序卸載。</span><span class="sxs-lookup"><span data-stu-id="6df66-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="6df66-107">若要完全移除執行中處理序的執行階段，您必須關閉該程序。</span><span class="sxs-lookup"><span data-stu-id="6df66-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df66-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6df66-108">See also</span></span>
- [<span data-ttu-id="6df66-109">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6df66-109">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
