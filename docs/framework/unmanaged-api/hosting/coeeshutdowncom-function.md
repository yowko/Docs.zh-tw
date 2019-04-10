---
title: CoEEShutDownCOM 函式
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ddef35b1b707cc5c962402e880923dca7d4d9d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208146"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="32909-102">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="32909-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="32909-103">強制 common language runtime (CLR) 版本所有的介面指標，它就會保存於執行階段可呼叫包裝函式 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="32909-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="32909-104">這有釋放 RCW 的所有快取的效果。</span><span class="sxs-lookup"><span data-stu-id="32909-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="32909-105">此全域函式已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="32909-105">This global function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="32909-106">相反地，針對特定執行階段使用的進入點。</span><span class="sxs-lookup"><span data-stu-id="32909-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32909-107">語法</span><span class="sxs-lookup"><span data-stu-id="32909-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="32909-108">備註</span><span class="sxs-lookup"><span data-stu-id="32909-108">Remarks</span></span>  
 <span data-ttu-id="32909-109">`CoEEShutDownCOM`函式第一次釋放所有的快取，和所有的內容中的所有 Rcw，則會移除任何現有的安裝程式中的終止通知。</span><span class="sxs-lookup"><span data-stu-id="32909-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="32909-110">沒有 DLL 卸載時發生。</span><span class="sxs-lookup"><span data-stu-id="32909-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="32909-111">此函式會影響所有的執行階段載入處理序。</span><span class="sxs-lookup"><span data-stu-id="32909-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="32909-112">開頭為[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]，在您想要影響的特定執行階段上的這個函式呼叫的進入點。</span><span class="sxs-lookup"><span data-stu-id="32909-112">Beginning with the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="32909-113">若要取得的進入點，請呼叫[iclrruntimeinfo:: Getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定"CoEEShutDownCOM 」。</span><span class="sxs-lookup"><span data-stu-id="32909-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32909-114">需求</span><span class="sxs-lookup"><span data-stu-id="32909-114">Requirements</span></span>  
 <span data-ttu-id="32909-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32909-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32909-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="32909-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32909-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="32909-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="32909-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="32909-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="32909-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32909-119">See also</span></span>

- [<span data-ttu-id="32909-120">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="32909-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
