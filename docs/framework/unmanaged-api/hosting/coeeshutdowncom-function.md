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
ms.openlocfilehash: 0d2b82bc056acd2e620461081b5f8c9d45fc152c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490640"
---
# <a name="coeeshutdowncom-function"></a><span data-ttu-id="cf17c-102">CoEEShutDownCOM 函式</span><span class="sxs-lookup"><span data-stu-id="cf17c-102">CoEEShutDownCOM Function</span></span>
<span data-ttu-id="cf17c-103">強制 common language runtime (CLR) 版本所有的介面指標，它就會保存於執行階段可呼叫包裝函式 (RCW)。</span><span class="sxs-lookup"><span data-stu-id="cf17c-103">Forces the common language runtime (CLR) to release all interface pointers it holds inside runtime callable wrappers (RCW).</span></span> <span data-ttu-id="cf17c-104">這有釋放 RCW 的所有快取的效果。</span><span class="sxs-lookup"><span data-stu-id="cf17c-104">This has the effect of releasing all RCW caches.</span></span> <span data-ttu-id="cf17c-105">在.NET Framework 4 中，此全域函式已被取代。</span><span class="sxs-lookup"><span data-stu-id="cf17c-105">This global function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="cf17c-106">相反地，針對特定執行階段使用的進入點。</span><span class="sxs-lookup"><span data-stu-id="cf17c-106">Instead, use the entry point for a specific runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf17c-107">語法</span><span class="sxs-lookup"><span data-stu-id="cf17c-107">Syntax</span></span>  
  
```  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf17c-108">備註</span><span class="sxs-lookup"><span data-stu-id="cf17c-108">Remarks</span></span>  
 <span data-ttu-id="cf17c-109">`CoEEShutDownCOM`函式第一次釋放所有的快取，和所有的內容中的所有 Rcw，則會移除任何現有的安裝程式中的終止通知。</span><span class="sxs-lookup"><span data-stu-id="cf17c-109">The `CoEEShutDownCOM` function first releases all the RCWs in all contexts and in all caches, and then removes any tear-down notification existing in setup.</span></span> <span data-ttu-id="cf17c-110">沒有 DLL 卸載時發生。</span><span class="sxs-lookup"><span data-stu-id="cf17c-110">No DLL unloading occurs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="cf17c-111">此函式會影響所有的執行階段載入處理序。</span><span class="sxs-lookup"><span data-stu-id="cf17c-111">This function affects all runtimes that are loaded into the process.</span></span>  
  
 <span data-ttu-id="cf17c-112">從.NET Framework 4 開始，在您想要影響的特定執行階段上的這個函式呼叫的進入點。</span><span class="sxs-lookup"><span data-stu-id="cf17c-112">Beginning with the .NET Framework 4, call the entry point for this function on the specific runtime you want to affect.</span></span> <span data-ttu-id="cf17c-113">若要取得的進入點，請呼叫[iclrruntimeinfo:: Getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法並指定"CoEEShutDownCOM 」。</span><span class="sxs-lookup"><span data-stu-id="cf17c-113">To get the entry point, call the [ICLRRuntimeInfo::GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) method and specify "CoEEShutDownCOM".</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf17c-114">需求</span><span class="sxs-lookup"><span data-stu-id="cf17c-114">Requirements</span></span>  
 <span data-ttu-id="cf17c-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cf17c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf17c-116">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf17c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf17c-117">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="cf17c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf17c-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf17c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf17c-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf17c-119">See also</span></span>

- [<span data-ttu-id="cf17c-120">中繼資料全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="cf17c-120">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
