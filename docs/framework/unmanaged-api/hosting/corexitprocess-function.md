---
title: CorExitProcess 函式
ms.date: 03/30/2017
api_name:
- CorExitProcess
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CorExitProcess
helpviewer_keywords:
- CorExitProcess function [.NET Framework hosting]
ms.assetid: a5cab4c6-990e-47f3-8798-cf422b791015
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a28b33f80299ae6fce34f9de66b6f7f1bc70ef6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490561"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="2a3e1-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="2a3e1-102">CorExitProcess Function</span></span>
<span data-ttu-id="2a3e1-103">關閉目前未受管理的處理序。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="2a3e1-104">此函式已被取代，在.NET Framework 4。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-104">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="2a3e1-105">使用[iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3e1-106">語法</span><span class="sxs-lookup"><span data-stu-id="2a3e1-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a3e1-107">參數</span><span class="sxs-lookup"><span data-stu-id="2a3e1-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="2a3e1-108">整數，指定處理序結束碼。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a3e1-109">備註</span><span class="sxs-lookup"><span data-stu-id="2a3e1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a3e1-110">從.NET Framework 4 中，`CorExitProcess`結束的處理程序中，而不只是舊版的 Api 有已繫結至執行階段中每個已啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-110">Beginning with the .NET Framework 4, `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a3e1-111">需求</span><span class="sxs-lookup"><span data-stu-id="2a3e1-111">Requirements</span></span>  
 <span data-ttu-id="2a3e1-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a3e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a3e1-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2a3e1-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2a3e1-114">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2a3e1-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2a3e1-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a3e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3e1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a3e1-116">See also</span></span>

- [<span data-ttu-id="2a3e1-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="2a3e1-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
