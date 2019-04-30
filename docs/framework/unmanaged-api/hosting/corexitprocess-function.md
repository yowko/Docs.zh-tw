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
ms.openlocfilehash: b95625cfe17b36c0244e6780a08dcf50ce50763d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985812"
---
# <a name="corexitprocess-function"></a><span data-ttu-id="94e4d-102">CorExitProcess 函式</span><span class="sxs-lookup"><span data-stu-id="94e4d-102">CorExitProcess Function</span></span>
<span data-ttu-id="94e4d-103">關閉目前未受管理的處理序。</span><span class="sxs-lookup"><span data-stu-id="94e4d-103">Shuts down the current unmanaged process.</span></span>  
  
 <span data-ttu-id="94e4d-104">此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="94e4d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="94e4d-105">使用[iclrmetahost:: Exitprocess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="94e4d-105">Use the [ICLRMetaHost::ExitProcess](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94e4d-106">語法</span><span class="sxs-lookup"><span data-stu-id="94e4d-106">Syntax</span></span>  
  
```  
void STDMETHODCALLTYPE CorExitProcess (   
  int  exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94e4d-107">參數</span><span class="sxs-lookup"><span data-stu-id="94e4d-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="94e4d-108">整數，指定處理序結束碼。</span><span class="sxs-lookup"><span data-stu-id="94e4d-108">An integer that specifies the process exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94e4d-109">備註</span><span class="sxs-lookup"><span data-stu-id="94e4d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94e4d-110">開頭[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，`CorExitProcess`結束的處理程序中，而不只是舊版的 Api 有已繫結至執行階段中每個已啟動執行階段。</span><span class="sxs-lookup"><span data-stu-id="94e4d-110">Beginning with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], `CorExitProcess` exits every started runtime in the process, not just the runtime to which the legacy APIs have been bound.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94e4d-111">需求</span><span class="sxs-lookup"><span data-stu-id="94e4d-111">Requirements</span></span>  
 <span data-ttu-id="94e4d-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94e4d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94e4d-113">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94e4d-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94e4d-114">**LIBRARY:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94e4d-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94e4d-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94e4d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e4d-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94e4d-116">See also</span></span>

- [<span data-ttu-id="94e4d-117">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="94e4d-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
