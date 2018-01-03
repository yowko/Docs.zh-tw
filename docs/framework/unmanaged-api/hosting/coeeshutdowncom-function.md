---
title: "CoEEShutDownCOM 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CoEEShutDownCOM
helpviewer_keywords: CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ae339310c2bfd186cae798ff603d69735abeefd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="a2947-102">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="a2947-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="a2947-103">強制執行 common language runtime (CLR) 版本保留在執行階段可呼叫包裝函式 (RCW) 內的所有介面指標。</span><span class="sxs-lookup"><span data-stu-id="a2947-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="a2947-104">這有釋放所有 RCW 快取的影響。</span><span class="sxs-lookup"><span data-stu-id="a2947-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="a2947-105">此全域函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a2947-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="a2947-106">相反地，使用特定的執行階段的進入點。</span><span class="sxs-lookup"><span data-stu-id="a2947-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2947-107">語法</span><span class="sxs-lookup"><span data-stu-id="a2947-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a2947-108">備註</span><span class="sxs-lookup"><span data-stu-id="a2947-108">Remarks</span></span>  
 <span data-ttu-id="a2947-109">`CoEEShutDownCOM`函式第一次釋放和所有的快取中所有內容中的所有 Rcw，，然後移除任何現有的安裝程式中的終止程式通知。</span><span class="sxs-lookup"><span data-stu-id="a2947-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="a2947-110">沒有 DLL 卸載就會發生。</span><span class="sxs-lookup"><span data-stu-id="a2947-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a2947-111">此函式會影響所有的執行階段載入處理序。</span><span class="sxs-lookup"><span data-stu-id="a2947-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="a2947-112">開頭為[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]，對您要影響的特定執行階段的這個函式呼叫的進入點。</span><span class="sxs-lookup"><span data-stu-id="a2947-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="a2947-113">若要取得的進入點，請呼叫[iclrruntimeinfo:: Getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定"CoEEShutDownCOM"。</span><span class="sxs-lookup"><span data-stu-id="a2947-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2947-114">需求</span><span class="sxs-lookup"><span data-stu-id="a2947-114">Requirements</span></span>  
 <span data-ttu-id="a2947-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a2947-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2947-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2947-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2947-117">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a2947-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2947-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2947-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2947-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2947-119">See Also</span></span>  
 [<span data-ttu-id="a2947-120">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a2947-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
