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
ms.openlocfilehash: 7d39c6fda6f159bfc937f62dc45d0d7ce37657f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687877"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="2eff6-102">CoUninitializeCor 函式</span><span class="sxs-lookup"><span data-stu-id="2eff6-102">CoUninitializeCor Function</span></span>

<span data-ttu-id="2eff6-103">`CoUninitializeCor` 已經過時。</span><span class="sxs-lookup"><span data-stu-id="2eff6-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2eff6-104">語法</span><span class="sxs-lookup"><span data-stu-id="2eff6-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="2eff6-105">備註</span><span class="sxs-lookup"><span data-stu-id="2eff6-105">Remarks</span></span>  

 <span data-ttu-id="2eff6-106">無法從進程卸載 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="2eff6-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="2eff6-107">若要從執行中的進程完全移除執行時間，您必須關閉該處理常式。</span><span class="sxs-lookup"><span data-stu-id="2eff6-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eff6-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eff6-108">See also</span></span>

- [<span data-ttu-id="2eff6-109">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2eff6-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
