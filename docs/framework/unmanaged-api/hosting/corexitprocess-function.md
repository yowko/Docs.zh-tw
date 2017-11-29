---
title: "CorExitProcess 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorExitProcess
helpviewer_keywords: CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75b35631bad5de46d48ed818c6f929f25a5f7e66
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corexitprocess-function"></a><span data-ttu-id="8a665-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="8a665-102">CorExitProcess Function</span></span>
<span data-ttu-id="8a665-103">關閉目前未受管理的程序。</span><span class="sxs-lookup"><span data-stu-id="8a665-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="8a665-104">此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a665-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="8a665-105">使用[iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="8a665-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a665-106">語法</span><span class="sxs-lookup"><span data-stu-id="8a665-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a665-107">參數</span><span class="sxs-lookup"><span data-stu-id="8a665-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="8a665-108">指定處理序結束碼的整數。</span><span class="sxs-lookup"><span data-stu-id="8a665-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a665-109">備註</span><span class="sxs-lookup"><span data-stu-id="8a665-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a665-110">開頭為[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，`CorExitProcess`結束的處理程序中，而不只是執行階段的舊版應用程式開發介面已繫結中每個已啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="8a665-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a665-111">需求</span><span class="sxs-lookup"><span data-stu-id="8a665-111">Requirements</span></span>  
 <span data-ttu-id="8a665-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a665-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a665-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a665-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a665-114">**程式庫：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a665-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a665-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a665-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a665-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a665-116">See Also</span></span>  
 [<span data-ttu-id="8a665-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="8a665-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
